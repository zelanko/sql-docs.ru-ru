---
title: "Планирование выполнения пакета служб SSIS в Azure | Документы Майкрософт"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 80fac355ad3ecc1486257651999be9d3f6ad30e6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="schedule-the-execution-of-an-ssis-package-on-azure"></a>Планирование выполнения пакета служб SSIS в Azure
Вы можете запланировать выполнение пакетов, хранящихся в базе данных каталога SSISDB на сервере базы данных SQL Azure, выбрав один из следующих вариантов планирования:
-   [SQL Server, агент](#agent)
-   [Задания обработки эластичных баз данных SQL](#elastic)
-   [Операция хранимой процедуры SQL Server для фабрики данных Azure](#sproc)

## <a name="agent"></a> Планирование пакета с помощью агента SQL Server

### <a name="prerequisite"></a>Предварительные требования

Прежде чем использовать агент SQL Server в локальной среде для планирования выполнения пакетов, хранящихся на сервере базы данных SQL Azure, необходимо добавить сервер базы данных SQL Database в качестве связанного сервера. Дополнительные сведения см. в разделах [Создание связанных серверов](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md) и [Связанные серверы](../../relational-databases/linked-servers/linked-servers-database-engine.md).

### <a name="create-a-sql-server-agent-job"></a>Создание задания агента SQL Server

Чтобы запланировать выполнение пакета с помощью локального агента SQL Server, создайте задание с шагом, на котором вызываются хранимые процедуры каталога служб SSIS `[catalog].[create_execution]` и затем `[catalog].[start_execution]`. Дополнительные сведения см. в разделе [Пакеты служб из заданий агента SQL Server](../packages/sql-server-agent-jobs-for-packages.md).

1.  В SQL Server Management Studio установите подключение к базе данных SQL Server в локальной среде, в которой требуется создать задание.

2.  Щелкните правой кнопкой мыши узел **Агент SQL Server**, выберите **Создать** и затем **Задание**, чтобы открыть диалоговое окно **Создание задания**.

3.  В диалоговом окне **Создание задания** перейдите на страницу **Шаги** и выберите команду **Создать**, чтобы открыть диалоговое окно **Создание шага задания**.

4.  В диалоговом окне **Создание шага задания** выберите `SSISDB` в поле **База данных**.

5.  В поле команды введите скрипт Transact-SQL, аналогичный приведенному в следующем примере:

    ```sql
    DECLARE @return_value int, @exe_id bigint 

    EXEC @return_value = [YourLinkedServer].[SSISDB].[catalog].[create_execution] 
    @folder_name=N'folderName', @project_name=N'projectName', 
    @package_name=N'packageName', @use32bitruntime=0, 
    @runinscaleout=1, @useanyworker=1, @execution_id=@exe_id OUTPUT 
 
    EXEC [YourLinkedServer].[SSISDB].[catalog].[start_execution] @execution_id=@exe_id

    GO
    ```

6.  Завершите настройку и планирование задания.

## <a name="elastic"></a> Планирование пакета с использованием заданий обработки эластичных баз данных SQL

Дополнительные сведения о заданиях обработки эластичных баз данных SQL см. в разделе [Управление облачными базами данных с горизонтальным масштабированием](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-overview).

### <a name="prerequisites"></a>Предварительные требования

Прежде чем использовать задания обработки эластичных баз данных для планирования пакетов SSIS, хранящихся в каталоге базы данных SSISDB на сервере базы данных SQL Azure, необходимо выполнить следующие действия:

1.  Установить и настроить компоненты для заданий обработки эластичных баз данных. Дополнительные сведения см. в разделе [Общие сведения об установке заданий обработки эластичных баз данных](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-service-installation).

2. Создать учетные данные уровня базы данных, которые задания смогут использовать для отправки команд в базу данных каталога SSIS. Дополнительные сведения см. в разделе [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

### <a name="create-an-elastic-job"></a>Создание задания обработки эластичных баз данных

Чтобы создать задание, используйте скрипт Transact-SQL, аналогичный приведенному в следующем примере:

```sql
-- Create Elastic Jobs target group 
EXEC jobs.sp_add_target_group 'TargetGroup' 

-- Add Elastic Jobs target group member 
EXEC jobs.sp_add_target_group_member @target_group_name='TargetGroup', 
    @target_type='SqlDatabase', @server_name='YourSQLDBServer.database.windows.net',
    @database_name='SSISDB' 

-- Add a job to schedule SSIS package execution
EXEC jobs.sp_add_job @job_name='ExecutePackageJob', @description='Description', 
    @schedule_interval_type='Minutes', @schedule_interval_count=60

-- Add a job step to create/start SSIS package execution using SSISDB catalog stored procedures
EXEC jobs.sp_add_jobstep @job_name='ExecutePackageJob', 
    @command=N'DECLARE @exe_id bigint 
        EXEC [SSISDB].[catalog].[create_execution]
            @folder_name=N''folderName'', @project_name=N''projectName'',
            @package_name=N''packageName'', @use32bitruntime=0,
            @runinscaleout=1, @useanyworker=1, 
            @execution_id=@exe_id OUTPUT         
        EXEC [SSISDB].[catalog].[start_execution] @exe_id, @retry_count=0', 
    @credential_name='YourDBScopedCredentials', 
    @target_group_name='TargetGroup' 

-- Enable the job schedule 
EXEC jobs.sp_update_job @job_name='ExecutePackageJob', @enabled=1, 
    @schedule_interval_type='Minutes', @schedule_interval_count=60 
```

## <a name="sproc"></a> Планирование пакета с использованием операции хранимой процедуры SQL Server для фабрики данных Azure

> [!IMPORTANT]
> Используйте скрипты JSON в следующем примере с операцией хранимой процедуры для фабрики данных Azure версии 1.

Чтобы запланировать выполнение пакета с использованием операции хранимой процедуры SQL Server для фабрики данных Azure, выполните следующие действия:

1.  Создайте фабрику данных.

2.  Создайте связанную службу для базы данных SQL, в которой размещается SSISDB.

3.  Создайте выходной набор данных, который управляет планированием.

4.  Создайте конвейер фабрики данных, который использует операцию хранимой процедуры SQL Server для выполнения пакета SSIS.

В этом разделе приводится обзор необходимых действий. Полное руководство по работе с фабрикой данных выходит за рамки этой статьи. Дополнительные сведения см. в разделе [Операция хранимой процедуры SQL Server](https://docs.microsoft.com/en-us/azure/data-factory/data-factory-stored-proc-activity).

### <a name="created-a-linked-service-for-the-sql-database-that-hosts-ssisdb"></a>Создание связанной службы для базы данных SQL, в которой размещается SSISDB
Связанная служба обеспечивает подключение фабрики данных к SSISDB.

```json
{
    "name": "AzureSqlLinkedService",
    "properties": {
        "description": "",
        "type": "AzureSqlDatabase",
        "typeProperties": {
            "connectionString": "Data Source = tcp: YourSQLDBServer.database.windows.net, 1433; Initial Catalog = SSISDB; User ID = YourUsername; Password = YourPassword; Integrated Security = False; Encrypt = True; Connect Timeout = 30"
        }
    }
}
```

### <a name="create-an-output-dataset"></a>Создание выходного набора данных
Выходной набор данных содержит сведения о планировании.

```json
{
    "name": "sprocsampleout",
    "properties": {
        "type": "AzureSqlTable",
        "linkedServiceName": "AzureSqlLinkedService",
        "typeProperties": {
            "tableName": "sampletable"
        },
        "availability": {
            "frequency": "Hour",
            "interval": 1
        }
    }
}
```
### <a name="create-a-data-factory-pipeline"></a>Создание конвейера фабрики данных
Конвейер использует операцию хранимой процедуры SQL Server для выполнения пакета SSIS.

```json
{
    "name": "SprocActivitySamplePipeline",
    "properties": {
        "activities": [{
            "name": "SprocActivitySample",
            "type": "SqlServerStoredProcedure",
            "typeProperties": {
                "storedProcedureName": "sp_executesql",
                "storedProcedureParameters": {
                    "stmt": "Transact-SQL script to create and start SSIS package execution using SSISDB catalog stored procedures"
                }
            },
            "outputs": [{
                "name": "sprocsampleout"
            }],
            "scheduler": {
                "frequency": "Hour",
                "interval": 1
            }
        }],
        "start": "2017-10-01T00:00:00Z",
        "end": "2017-10-01T05:00:00Z",
        "isPaused": false
    }
}
```

Вам не нужно создавать новую хранимую процедуру для инкапсуляции команд Transact-SQL, необходимых для создания и запуска выполнения пакета SSIS. Вы можете передать весь скрипт в качестве значения параметра `stmt` в приведенном выше примере JSON. Пример скрипта:

```sql
-- T-SQL script to create and start SSIS package execution using SSISDB catalog stored procedures
DECLARE @return_value INT,@exe_id BIGINT,@err_msg NVARCHAR(150)

-- Create the exectuion
EXEC @return_value=[SSISDB].[catalog].[create_execution] @folder_name=N'folderName', @project_name=N'projectName', @package_name=N'packageName', @use32bitruntime=0, @runinscaleout=1,@useanyworker=1, @execution_id=@exe_id OUTPUT

-- To synchronize SSIS package execution, set the SYNCHRONIZED execution parameter
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @exe_id, @object_type=50, @parameter_name=N'SYNCHRONIZED', @parameter_value=1

-- Start the execution                                                         
EXEC [SSISDB].[catalog].[start_execution] @execution_id=@exe_id,@retry_count=0
                                          
-- Raise an error for unsuccessful package execution
-- Execution status values include the following:
-- created (1)
-- running (2)
-- canceled (3)
-- failed (4)
-- pending (5)
-- ended unexpectedly (6)
-- succeeded (7)
-- stopping (8)
-- completed (9) 
IF(SELECT [status]
   FROM [SSISDB].[catalog].[executions]
   WHERE execution_id=@exe_id)<>7
BEGIN
    SET @err_msg=N'Your package execution did not succeed for execution ID: ' + CAST(@exe_id AS NVARCHAR(20))
    RAISERROR(@err_msg,15,1)
END
GO
```

Дополнительные сведения о коде в этом скрипте см. в разделе [Развертывание и выполнение пакетов служб SSIS с помощью хранимых процедур](../packages/deploy-integration-services-ssis-projects-and-packages.md#deploy-and-execute-ssis-packages-using-stored-procedures).

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения об агенте SQL Server см. в разделе [Пакеты служб из заданий агента SQL Server](../packages/sql-server-agent-jobs-for-packages.md).

Дополнительные сведения о заданиях обработки эластичных баз данных SQL см. в разделе [Управление облачными базами данных с горизонтальным масштабированием](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-overview).
