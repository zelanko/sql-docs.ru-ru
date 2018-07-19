---
title: Создание и запуск задания для SQL Server в Linux | Документация Майкрософт
description: Этом руководстве показано, как запустить задание агента SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 1d93d95e-9c89-4274-9b3f-fa2608ec2792
ms.openlocfilehash: 162015772bb54023816fcc7d911ca34fbd4a3ac7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38001806"
---
# <a name="create-and-run-sql-server-agent-jobs-on-linux"></a>Создание и запуск задания агента SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Задания SQL Server используются регулярно выполнять ту же последовательность команд в базе данных SQL Server. Этот учебник содержит пример того, как создать задание агента SQL Server в Linux с помощью Transact-SQL и SQL Server Management Studio (SSMS).

> [!div class="checklist"]
> * Установка агента SQL Server в Linux
> * Создать задание для выполнения ежедневных резервных копий базы данных
> * Планирование и запуск задания
> * Выполните те же действия в среде SSMS (необязательно)

Известные проблемы с агентом SQL Server в Linux см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

## <a name="prerequisites"></a>предварительные требования

Для работы с этим руководством требуются следующие компоненты:

* Компьютер Linux со следующими компонентами:
  * SQL Server 2017 ([RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), или [Ubuntu](quickstart-install-connect-ubuntu.md)) с помощью средства командной строки.

Следующие компоненты являются необязательными.

* Компьютер Windows с помощью SSMS:
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) для дополнительных шагов SSMS.

## <a name="enable-sql-server-agent"></a>Включить агент SQL Server

Использовать агент SQL Server в Linux, необходимо сначала включить агент SQL Server на компьютере с уже установленным SQL Server 2017.

1. Чтобы включить агент SQL Server, выполните следующие шаги.
  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
  ```

1. Перезапустите SQL Server с помощью следующей команды:
  ```bash
  sudo systemctl restart mssql-server
  ```

> [!NOTE]
> Начиная с накопительным пакетом обновления 4 для SQL Server 2017, агента SQL Server входит в состав **mssql-server** упаковки и отключен по умолчанию. Для настройки агента до посещения накопительным пакетом обновления 4, [Установка агента SQL Server в Linux](sql-server-linux-setup-sql-agent.md).

## <a name="create-a-sample-database"></a>Создание образца базы данных

Выполните следующие действия для создания образца базы данных с именем **SampleDB**. Эта база данных используется для ежедневного задания архивации.

1. На компьютере Linux откройте сеанс терминала bash.

1. Используйте **sqlcmd** для запуска Transact-SQL **CREATE DATABASE** команды.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'CREATE DATABASE SampleDB'
   ```

1. Убедитесь, что создан посредством перечисления баз данных на сервере базы данных.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'SELECT Name FROM sys.Databases'
   ```

## <a name="create-a-job-with-transact-sql"></a>Создание задания с помощью Transact-SQL

Следующие действия с помощью команд Transact-SQL, создайте задание агента SQL Server в Linux. Задание выполняется ежедневной резервной копии образца базы данных, **SampleDB**.

> [!TIP]
> Можно использовать любой клиент T-SQL для выполнения этих команд. Например, на платформе Linux можно использовать [sqlcmd](sql-server-linux-setup-tools.md) или [Visual Studio Code](sql-server-linux-develop-use-vscode.md). С удаленного сервера Windows можно также выполнять запросы в SQL Server Management Studio (SSMS) или использовать пользовательский интерфейс для управления задания, который описан в следующем разделе.

1. Используйте [sp_add_job](../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md) Создание задания с именем `Daily SampleDB Backup`.

   ```sql
   -- Adds a new job executed by the SQLServerAgent service
   -- called 'Daily SampleDB Backup'
   USE msdb ;
   GO
   EXEC dbo.sp_add_job
      @job_name = N'Daily SampleDB Backup' ;
   GO
   ```

1. Вызовите [sp_add_jobstep](../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md) Создание шага задания, которое создает резервную копию `SampleDB` базы данных.

   ```sql
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

1. Затем создайте ежедневное расписание для задания с [sp_add_schedule](../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md).

   ```sql
   -- Creates a schedule called 'Daily'
   EXEC dbo.sp_add_schedule
      @schedule_name = N'Daily SampleDB',
      @freq_type = 4,
      @freq_interval = 1,
      @active_start_time = 233000 ;
   USE msdb ;
   GO
   ```

1. Присоединение расписания к заданию, используя [sp_attach_schedule](../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md).

   ```sql
   -- Sets the 'Daily' schedule to the 'Daily SampleDB Backup' Job
   EXEC sp_attach_schedule
      @job_name = N'Daily SampleDB Backup',
      @schedule_name = N'Daily SampleDB';
   GO
   ```

1. Используйте [sp_add_jobserver](../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md) для назначения задания на целевом сервере. В этом примере целью является локальный сервер.

   ```sql
   EXEC dbo.sp_add_jobserver
      @job_name = N'Daily SampleDB Backup',
      @server_name = N'(LOCAL)';
   GO
   ```
1. Запустить задание с [sp_start_job](../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md).

   ```sql
   EXEC dbo.sp_start_job N' Daily SampleDB Backup' ;
   GO
   ```

## <a name="create-a-job-with-ssms"></a>Создание задания с помощью SSMS

Можно также создать и управлять заданиями удаленно с помощью SQL Server Management Studio (SSMS) на Windows.

1. Запустите SSMS на Windows и подключитесь к экземпляру SQL Server для Linux. Дополнительные сведения см. в разделе [управления SQL Server в Linux с помощью SSMS](sql-server-linux-manage-ssms.md).

1. Убедитесь, что вы создали образец базы данных с именем **SampleDB**.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-0.png" alt="Create a SampleDB database" style="width: 550px;"/>

1. Убедитесь, что агент SQL выполнено [установлен](sql-server-linux-setup-sql-agent.md) и правильно настроен. Найдите знак «плюс» рядом с агентом SQL Server в обозревателе объектов. Если агент SQL Server не включена, попробуйте перезагрузить **mssql-server** службы на платформе Linux.

   ![Убедитесь, что был установлен агент SQL Server](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-1.png)

1. Создайте новое задание.

   ![Создание нового задания](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-2.png)

1. Присвойте заданию имя и создайте в шаг задания.

   ![Создание шага задания](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-3.png)

1. Укажите, какая подсистема, вы хотите использовать, и действия необходимо выполнить шаг задания.

   ![Подсистемы задания](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-4.png)

   ![Действие шага задания](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-5.png)

1. Создайте новое расписание задания.

   ![расписание заданий;](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-6.png)

   ![расписание заданий;](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-8.png)

1. Запуск задания.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-9.png" alt="Start the SQL Server Agent job" style="width: 550px;"/>

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как:

> [!div class="checklist"]
> * Установка агента SQL Server в Linux
> * Используйте Transact-SQL и системные хранимые процедуры для создания заданий
> * Создать задание, которое выполняет ежедневное резервное копирование базы данных
> * Создание и управление заданиями с помощью пользовательского интерфейса среды SSMS

Изучим других возможностей для создания и управления заданиями:

> [!div class="nextstepaction"]
>[Документация по агенту SQL Server](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent)
