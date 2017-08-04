---
title: "Создание и запуск задания для SQL Server в Linux | Документы Microsoft"
description: "Этот учебник показывает, как для запуска задания агента SQL Server в Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1d93d95e-9c89-4274-9b3f-fa2608ec2792
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3ffb76838940f42d7a696e1c17f227517d89012d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---

# <a name="create-and-run-sql-server-agent-jobs-on-linux"></a>Создание и запуск задания агента SQL Server в Linux
Задания SQL Server используются для выполнения регулярных та же последовательность команд в базе данных SQL Server. В этом разделе приведены примеры создания задания агента SQL Server для Linux с помощью Transact-SQL и SQL Server Management Studio (SSMS).

Известные проблемы с агентом SQL Server в этом выпуске см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

## <a name="prerequisites"></a>Предварительные требования 
Для создания и запуска заданий, необходимо сначала установить службу агента SQL Server. Инструкции по установке см. в разделе [раздел установки агента SQL Server](sql-server-linux-setup-sql-agent.md).

## <a name="create-a-job-with-transact-sql"></a>Создание задания с помощью Transact-SQL

Ниже приведен пример того, как создать задание агента SQL Server в Linux с помощью команды Transact-SQL. Эти задания в этом примере выполняется ежедневного резервного копирования на образце базы данных `SampleDB`. 


> [!TIP]
> Можно использовать любой клиент T-SQL для выполнения этих команд. Например, в Linux можно использовать [sqlcmd](sql-server-linux-setup-tools.md) или [кода Visual Studio](sql-server-linux-develop-use-vscode.md). С удаленного сервера Windows можно выполнять запросы в SQL Server Management Studio (SSMS) или использовать пользовательский интерфейс для управления заданиями, как описано в следующем разделе.

1. **Создать задание**. В следующем примере используется [sp_add_job](https://msdn.microsoft.com/library/ms182079.aspx) Создание задания с именем `Daily AdventureWorks Backup`.

    ```tsql
     -- Adds a new job executed by the SQLServerAgent service 
     -- called 'Daily SampleDB Backup'  
     CREATE DATABASE SampleDB
     USE msdb ;  
     GO  
     EXEC dbo.sp_add_job  
         @job_name = N'Daily SampleDB Backup' ;  
     GO

    ```

2. **Добавьте один или несколько шагов задания**. В следующем сценарии Transact-SQL используется [sp_add_jobstep](https://msdn.microsoft.com/library/ms187358.aspx) Создание шага задания, которое создает резервную копию `AdventureWlorks2014` базы данных.

    ```tsql
    -- Adds a step (operation) to the job  
    EXEC sp_add_jobstep  
      @job_name = N'Daily SampleDB Backup',  
      @step_name = N'Backup database',  
      @subsystem = N'TSQL',  
      @command = N'BACKUP DATABASE SampleDB TO DISK = \
      N''/var/opt/mssql/data/SampleDB.bak'' WITH NOFORMAT, NOINIT, \
              NAME = ''SampleDB-full'', SKIP, NOREWIND, NOUNLOAD, STATS = 10',   
      @retry_attempts = 5,  
      @retry_interval = 5 ;  
    GO
    ```

3. **Создание расписания задания**. В этом примере используется [sp_add_schedule](https://msdn.microsoft.com/library/ms366342.aspx) Создание ежедневного расписания для задания.

    ```tsql
    -- Creates a schedule called 'Daily'  
    EXEC dbo.sp_add_schedule  
     @schedule_name = N'Daily SampleDB',  
     @freq_type = 4,  
     @freq_interval = 1,
     @active_start_time = 233000 ;  
   USE msdb ;  
   GO
    ```

4. **Присоединить расписание заданий для задания**. Используйте [sp_attach_schedule](https://msdn.microsoft.com/library/ms186766.aspx) присоединение расписания задания к заданию.

    ```tsql
    -- Sets the 'Daily' schedule to the 'Daily AdventureWorks Backup' Job  
    EXEC sp_attach_schedule  
     @job_name = N'Daily SampleDB Backup',  
     @schedule_name = N'Daily SampleDB';  
    GO
    ```

5. **Назначение задания на целевом сервере**. Назначение задания на целевом сервере с [sp_add_jobserver](https://msdn.microsoft.com/library/ms178625.aspx). В этом примере локальный сервер является целевым.

    ```tsql
    EXEC dbo.sp_add_jobserver  
     @job_name = N'Daily SampleDB Backup',  
     @server_name = N'(LOCAL)';  
    GO
    ```
6. **Запустить задание**. 

    ```tsql
    EXEC dbo.sp_start_job N' Daily SampleDB Backup' ;
    GO
    ```
## <a name="create-a-job-with-ssms"></a>Создание задания с помощью SSMS

Можно также создать и управлять заданиями удаленно с помощью SQL Server Management Studio (SSMS) в Windows.

1. **Запустите SSMS в Windows и подключитесь к экземпляру SQL Server для Linux.** Дополнительные сведения см. в разделе [управления SQL Server в Linux с помощью SSMS](sql-server-linux-develop-use-ssms.md).

1. **Создать новую базу данных с именем SampleDB**.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-0.png" alt="Create a SampleDB database" style="width: 550px;"/>

2. **Убедитесь, что агент SQL был установлен и настроен правильно.** Найдите знак «плюс» рядом с агентом SQL Server в обозревателе объектов. Если агент SQL Server не установлен, в разделе [установки агента SQL Server в Linux](sql-server-linux-setup-sql-agent.md).

    ![Убедитесь, что был установлен агент SQL Server](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-1.png)


3. **Создайте новое задание.**

    ![Создать новое задание](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-2.png)


4. **Имя задания и создайте вашего шаг задания.**

    ![Создание шага задания](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-3.png)


5. **Укажите, какие подсистемы, которые вы хотите использовать, и действия необходимо выполнить шаг задания.**

    ![Задание подсистемы](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-4.png)

    ![Действие шага задания](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-5.png)

6. **Создайте новое расписание задания.**

    ![расписание заданий;](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-6.png)
  
    ![расписание заданий;](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-8.png)

7. **Запустите задание.**

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-9.png" alt="Start the SQL Server Agent job" style="width: 550px;"/>

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о создании и управлении заданий агента SQL Server см. в разделе [агента SQL Server](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent).

