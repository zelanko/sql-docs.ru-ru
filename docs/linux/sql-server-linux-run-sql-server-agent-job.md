---
title: Создание и запуск заданий для SQL Server в Linux
description: В этом руководстве показано, как запустить задание агента SQL Server в Linux.
author: VanMSFT
ms.author: vanto
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1d93d95e-9c89-4274-9b3f-fa2608ec2792
ms.openlocfilehash: 1bad76e2cec68ba2e4c54f698c44e38590efd344
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883063"
---
# <a name="create-and-run-sql-server-agent-jobs-on-linux"></a>Создание и запуск заданий агента SQL Server в Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Задания SQL Server используются для регулярного выполнения одинаковой последовательности команд в базе данных SQL Server. В этом учебнике представлен пример создания задания агента SQL Server в Linux с помощью Transact-SQL и SQL Server Management Studio (SSMS).

> [!div class="checklist"]
> * Установка агента SQL Server в Linux
> * Создание задания для выполнения ежедневного резервного копирования базы данных
> * Планирование и запуск задания
> * Выполнение тех же действий в SSMS (необязательно)

Известные проблемы с агентом SQL Server в Linux см. в [заметках о выпуске](sql-server-linux-release-notes.md).

## <a name="prerequisites"></a>предварительные требования

Для работы с этим руководством необходимо выполнить следующие условия.

* Компьютер Linux со следующими необходимыми компонентами:
  * SQL Server ([RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md) или [Ubuntu](quickstart-install-connect-ubuntu.md)) с программами командной строки.

Следующие компоненты являются необязательными.

* Компьютер Windows с SSMS:
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) для дополнительных действия с SSMS.

## <a name="enable-sql-server-agent"></a>Включение агента SQL Server

Чтобы использовать агент SQL Server в Linux, нужно сначала включить его на компьютере, где уже установлен SQL Server.

1. Чтобы включить агент SQL Server, сделайте следующее.
  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
  ```

1. Перезапустите SQL Server с помощью следующей команды.
  ```bash
  sudo systemctl restart mssql-server
  ```

> [!NOTE]
> Начиная с версии SQL Server 2017 с накопительным пакетом обновления 4, агент SQL Server включается в пакет **mssql-server** и по умолчанию отключен. Сведения о настройке агента в версиях, предшествующих накопительному пакету обновления 4, см. в статье [Установка агента SQL Server в Linux](sql-server-linux-setup-sql-agent.md).

## <a name="create-a-sample-database"></a>Создание образца базы данных

Чтобы создать образец базы данных с именем **SampleDB**, выполните указанные ниже действия. Эта база данных используется для задания ежедневного резервного копирования.

1. На компьютере Linux откройте сеанс терминала bash.

1. Используйте **sqlcmd** для выполнения команды **CREATE DATABASE** Transact-SQL.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'CREATE DATABASE SampleDB'
   ```

1. Убедитесь, что база данных создана, выведя список баз данных на сервере.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'SELECT Name FROM sys.Databases'
   ```

## <a name="create-a-job-with-transact-sql"></a>Создание задания с помощью Transact-SQL

Приведенные ниже шаги позволяют создать задание агента SQL Server в Linux с помощью команд Transact-SQL. Это задание выполняет ежедневное резервное копирование образца базы данных **SampleDB**.

> [!TIP]
> Для выполнения этих команд можно использовать любой клиент T-SQL. Например, в Linux можно использовать [sqlcmd](sql-server-linux-setup-tools.md) или [Visual Studio Code](sql-server-linux-develop-use-vscode.md). С удаленного сервера Windows Server вы также можете выполнять запросы в SQL Server Management Studio (SSMS) или использовать пользовательский интерфейс для управления заданиями, как описано в следующем разделе.

1. Используйте [sp_add_job](../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md) для создания задания `Daily SampleDB Backup`.

   ```sql
   -- Adds a new job executed by the SQLServerAgent service
   -- called 'Daily SampleDB Backup'
   USE msdb ;
   GO
   EXEC dbo.sp_add_job
      @job_name = N'Daily SampleDB Backup' ;
   GO
   ```

1. Вызовите [sp_add_jobstep](../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md), чтобы создать шаг задания, создающий резервную копию базы данных `SampleDB`.

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

1. Затем создайте ежедневное расписание для задания с помощью [sp_add_schedule](../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md).

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

1. Подключите расписание задания к заданию с помощью [sp_attach_schedule](../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md).

   ```sql
   -- Sets the 'Daily' schedule to the 'Daily SampleDB Backup' Job
   EXEC sp_attach_schedule
      @job_name = N'Daily SampleDB Backup',
      @schedule_name = N'Daily SampleDB';
   GO
   ```

1. Используйте [sp_add_jobserver](../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md), чтобы назначить задание целевому серверу. В этом примере целевым объектом является локальный сервер.

   ```sql
   EXEC dbo.sp_add_jobserver
      @job_name = N'Daily SampleDB Backup',
      @server_name = N'(LOCAL)';
   GO
   ```
1. Запустите задание с помощью [sp_start_job](../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md).

   ```sql
   EXEC dbo.sp_start_job N' Daily SampleDB Backup' ;
   GO
   ```

## <a name="create-a-job-with-ssms"></a>Создание задания с использованием SSMS

Кроме того, с помощью SQL Server Management Studio (SSMS) в Windows можно удаленно создавать задания и управлять ими.

1. Запустите SSMS в Windows и подключитесь к своему экземпляру SQL Server в Linux. Дополнительные сведения см. в статье [Управление SQL Server в Linux с помощью SSMS](sql-server-linux-manage-ssms.md).

1. Убедитесь, чтобы создан образец базы данных с именем **SampleDB**.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-0.png" alt="Create a SampleDB database" style="width: 550px;"/>

1. Убедитесь, что агент SQL [установлен](sql-server-linux-setup-sql-agent.md) и настроен правильно. Найдите знак "плюс" рядом с агентом SQL Server в обозревателе объектов. Если агент SQL Server не включен, попробуйте перезапустить службу **mssql-server** в Linux.

   ![Проверка установки агента SQL Server](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-1.png)

1. Создайте задание.

   ![Создание задания](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-2.png)

1. Присвойте заданию имя и создайте шаг задания.

   ![Создание шага задания](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-3.png)

1. Укажите подсистему, которую вы хотите использовать, и действие, которое должен выполнить шаг задания.

   ![Подсистема заданий](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-4.png)

   ![Действие шага задания](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-5.png)

1. Создайте расписание задания.

   ![расписание заданий;](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-6.png)

   ![расписание заданий;](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-8.png)

1. Запустите ваше задание.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-9.png" alt="Start the SQL Server Agent job" style="width: 550px;"/>

## <a name="next-steps"></a>Next Steps

В этом руководстве вы узнали, как выполнять следующие задачи:

> [!div class="checklist"]
> * Установка агента SQL Server в Linux
> * Использование Transact-SQL и системных хранимых процедур для создания заданий
> * Создание задания, выполняющего ежедневное резервное копирование базы данных
> * Использование пользовательского интерфейса SSMS для создания заданий и управления ими

Далее вы можете изучить другие возможности для создания заданий и управления ими.

> [!div class="nextstepaction"]
>[Документация по агенту SQL Server](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent)
