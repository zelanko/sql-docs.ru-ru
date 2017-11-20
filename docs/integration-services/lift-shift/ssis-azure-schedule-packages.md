---
title: "Запланировать выполнение пакета служб SSIS в Azure | Документы Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2f28400200105e8e63f787cbcda58c183ba00da5
ms.openlocfilehash: 2130e68d5e29671a2881d8762666cf852ff51259
ms.contentlocale: ru-ru
ms.lasthandoff: 10/18/2017

---
# <a name="schedule-the-execution-of-an-ssis-package-on-azure"></a>Запланировать выполнение пакета служб SSIS в Azure
Можно запланировать выполнение пакетов, хранящихся в базе данных каталога SSISDB на сервере базы данных SQL Azure, выбрав один из следующих параметров планирования:
-   [SQL Server, агент](#agent)
-   [Заданий эластичных баз данных SQL](#elastic)
-   [Действие хранимую процедуру для фабрики SQL Azure данные сервера](#sproc)

## <a name="agent"></a>Планирование пакета с помощью агента SQL Server

### <a name="prerequisite"></a>Предварительные требования

Прежде чем агент SQL Server на локальном компьютере можно использовать для планирования выполнения пакетов, хранящихся на сервере базы данных SQL Azure, необходимо добавить базу данных SQL server в качестве связанного сервера. Дополнительные сведения см. в разделе [создавать связанные серверы](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md) и [связанные серверы](../../relational-databases/linked-servers/linked-servers-database-engine.md).

### <a name="create-a-sql-server-agent-job"></a>Создание задания агента SQL Server

Чтобы запланировать запуск пакета с помощью агента SQL Server на локальном компьютере, создание задания с шага задания, который вызывает каталога служб SSIS хранимых процедур `[catalog].[create_execution]` и затем `[catalog].[start_execution]`. Дополнительные сведения см. в разделе [заданий агента SQL Server для пакетов](../packages/sql-server-agent-jobs-for-packages.md).

1.  В SQL Server Management Studio подключитесь к базы данных SQL Server в локальной среде, на котором нужно создать задание.

2.  Щелкните правой кнопкой мыши **агента SQL Server** выберите **New**и выберите **задания** Открытие **новое задание** диалоговое окно.

3.  В **новое задание** выберите **действия** страницы, а затем выберите **New** Открытие **новый шаг задания** диалоговое окно.

4.  В **новый шаг задания** выберите `SSISDB` как **базы данных.**

5.  В поле Команда введите сценарий Transact-SQL, аналогичный сценарий, показанный в следующем примере:

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

## <a name="elastic"></a>Планирование пакета с заданий эластичных баз данных SQL

Дополнительные сведения о эластичной задания в базе данных SQL см. в разделе [базы данных горизонтально масштабируемого облака управление](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-overview).

### <a name="prerequisites"></a>Предварительные требования

Перед эластичной заданий можно использовать для планирования пакетов служб SSIS, хранимые в базе данных каталога SSISDB на сервере базы данных SQL Azure, необходимо выполнить следующие действия:

1.  Установка и настройка компонентов заданий эластичных баз данных. Дополнительные сведения см. в разделе [Общие сведения об установке эластичной базы данных заданий](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-service-installation).

2. Создание уровня базы данных учетных данных, используемых заданиями для отправки команд в базе данных каталога служб SSIS. Дополнительные сведения см. в разделе [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

### <a name="create-an-elastic-job"></a>Создать задание эластичной

Создание задания с помощью скрипта Transact-SQL, аналогично сценарий, показанный в следующем примере:

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

## <a name="sproc"></a>Планирование пакета с действием хранимую процедуру для фабрики SQL Azure данные сервера

> [!IMPORTANT]
> Использование сценариев JSON в следующем примере с фабрикой данных Azure версии 1 действия хранимой процедуры.

Чтобы запланировать запуск пакета с действием хранимую процедуру для фабрики SQL Azure данные сервера, выполните следующие действия:

1.  Создайте фабрику данных.

2.  Создать связанную службу для базы данных SQL, на котором размещена SSISDB.

3.  Создайте выходной набор данных, который управляет планированием.

4.  Создание конвейера фабрики данных, который использует действие хранимую процедуру SQL Server для запуска пакета служб SSIS.

Этот раздел содержит обзор этих действий. Весь учебник фабрики данных выходит за рамки данной статьи. Дополнительные сведения см. в разделе [действия хранимой процедуры SQL Server](https://docs.microsoft.com/en-us/azure/data-factory/data-factory-stored-proc-activity).

### <a name="created-a-linked-service-for-the-sql-database-that-hosts-ssisdb"></a>Создать связанную службу для базы данных SQL, на котором размещена SSISDB
Связанная служба позволяет подключиться к SSISDB фабрики данных.

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

### <a name="create-an-output-dataset"></a>Создайте набор данных выходных данных
Выходной набор данных содержит данные расписания.

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
Конвейер используется действие хранимую процедуру SQL Server для запуска пакета служб SSIS.

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

Не требуется создавать новую хранимую процедуру для инкапсуляции команд Transact-SQL, необходимые для создания и запустить выполнение пакета служб SSIS. В качестве значения можно предоставить всему скрипту `stmt` параметр в предыдущем примере JSON. Ниже приведен пример сценария:

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

Дополнительные сведения о коде в этом сценарии см. в разделе [развертывание и выполнение пакетов служб SSIS с помощью хранимых процедур](../packages/deploy-integration-services-ssis-projects-and-packages.md#deploy-and-execute-ssis-packages-using-stored-procedures).

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения об агенте SQL Server см. в разделе [заданий агента SQL Server для пакетов](../packages/sql-server-agent-jobs-for-packages.md).

Дополнительные сведения о эластичной задания в базе данных SQL см. в разделе [базы данных горизонтально масштабируемого облака управление](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-overview).

