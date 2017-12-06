---
title: "Миграция базы данных SQL Server с Windows и Linux | Документы Microsoft"
description: "Этот учебник демонстрирует создайте резервную копию базы данных SQL Server в Windows и восстановите ее на компьютер Linux под управлением 2017 г. SQL Server."
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/16/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 9ac64d1a-9fe5-446e-93c3-d17b8f55a28f
ms.workload: On Demand
ms.openlocfilehash: 6d54a849630bece0fba6456a516cbd68aecf2eb5
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restore"></a>Миграция базы данных SQL Server с Windows и Linux с помощью резервного копирования и восстановления

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

SQL Server резервного копирования, и функция восстановления рекомендуется использовать для миграции базы данных из SQL Server в Windows 2017 г. SQL Server в Linux. В этом учебнике поможет выполнить шаги, необходимые для перемещения базы данных Linux с помощью резервного копирования и восстановления методы.

> [!div class="checklist"]
> * Создать файл резервной копии в Windows с помощью SSMS
> * Установка оболочки Bash в Windows
> * Перемещение файла резервной копии для Linux в оболочке Bash
> * Восстановление резервной копии файла в Linux с помощью Transact-SQL
> * Выполните запрос, чтобы проверка миграции

## <a name="prerequisites"></a>Предварительные требования

С этим учебником требуются следующие необходимые компоненты:

* Компьютер Windows со следующими:
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions) установлен.
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) установлен.
  * Целевой базы данных для миграции.

* Компьютер Linux с установлены следующие компоненты:
  * 2017 г. SQL Server ([RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), или [Ubuntu](quickstart-install-connect-ubuntu.md)) с помощью средства командной строки.

## <a name="create-a-backup-on-windows"></a>Создание резервной копии в Windows

Существует несколько способов создания файла резервной копии базы данных в Windows. В следующих действиях используется SQL Server Management Studio (SSMS).

1. Запуск **SQL Server Management Studio** на компьютере Windows.

1. В диалоговом окне соединения введите **localhost**.

1. В обозревателе объектов разверните **баз данных**.

1. Щелкните правой кнопкой мыши целевой базы данных, выберите **задачи**, а затем нажмите кнопку **создайте резервную копию...** .

   ![Использование среды SSMS для создания файла резервной копии](./media/sql-server-linux-migrate-restore-database/ssms-create-backup.png)

1. В **резервное копирование копии базы данных** диалогового окна, убедитесь, что **тип резервной копии** — **полного** и **создать резервную копию на** — **диск**. Обратите внимание, имя и расположение файла. Например, база данных с именем **YourDB** на SQL Server 2016 имеет путь по умолчанию для резервной копии из `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak`.

1. Нажмите кнопку **ОК** в резервную копию базы данных.

> [!NOTE]
> Другой вариант — выполнить запрос Transact-SQL для создания файла резервной копии. Следующие команды Transact-SQL выполняются те же действия, как предыдущие шаги для базы данных называется **YourDB**:
>
> ```sql
> BACKUP DATABASE [YourDB] TO  DISK =
> N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak'
> WITH NOFORMAT, NOINIT, NAME = N'YourDB-Full Database Backup',
> SKIP, NOREWIND, NOUNLOAD, STATS = 10
> GO
> ```

## <a name="install-a-bash-shell-on-windows"></a>Установка оболочки Bash в Windows

Чтобы восстановить базу данных, сначала следует перенести файл резервной копии на компьютере Windows на целевом компьютере Linux. В этом учебнике мы переместите файл в Linux из оболочки Bash (окно терминала) под управлением Windows.

1. Установите на компьютер Windows, которая поддерживает оболочке Bash **scp** (безопасный копирования) и **ssh** команд (удаленного имени входа). Две следующие примеры.

   * [Подсистемы Windows для Linux](https://msdn.microsoft.com/commandline/wsl/about) (Windows 10)
   * В оболочке Git Bash ([https://git-scm.com/downloads](https://git-scm.com/downloads))

1. Откройте сеанс Bash в Windows.

## <a id="scp"></a>Скопируйте файл резервной копии в Linux

1. В сеансе Bash перейдите в каталог, содержащий файл архива. Например:

   ```bash
   cd 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\'
   ```

1. Используйте **scp** команду, чтобы переместить файл на целевом компьютере Linux. Следующий пример передачи **YourDB.bak** для домашнего каталога *user1* на сервер Linux с IP-адресом *192.0.2.9*:

   ```bash
   scp YourDB.bak user1@192.0.2.9:./
   ```
   ![Команда точку подключения службы](./media/sql-server-linux-migrate-restore-database/scp-command.png)

> [!TIP]
> Существуют альтернативы использованию scp для передачи файлов. Один является применение [Samba](https://help.ubuntu.com/community/Samba) для настройки сетевой папке SMB между Windows и Linux. Пошаговое руководство Ubuntu см. в разделе [Создание сетевой папки через Samba](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!). После установки, его можно получить в виде файла сети общую папку из Windows, таких как  **\\ \\machinenameorip\\совместное использование**.

## <a name="move-the-backup-file-before-restoring"></a>Переместите файл резервной копии перед восстановлением

В этот момент файл резервной копии находится на сервер Linux в домашнем каталоге пользователя. Перед восстановлением базы данных в SQL Server, резервное копирование необходимо поместить в подкаталоге **/var/opt/mssql**.

1. В одном сеансе Windows Bash удаленного подключения на целевом компьютере Linux с **ssh**. Следующий пример соединяет компьютер Linux **192.0.2.9** имени пользователя **user1**.

   ```bash
   ssh user1@192.0.2.9
   ```

   Команды выполняются на удаленном сервере Linux.

1. Перейдите в режим суперпользователя.

   ```bash
   sudo su
   ```

1. Создайте новый каталог резервного копирования. Если каталог уже существует, параметр -p не выполняет никаких действий.

   ```bash
   mkdir -p /var/opt/mssql/backup
   ```

1. Переместите файл резервной копии к этому каталогу. В следующем примере файл резервной копии находится в домашнем каталоге *user1*. Измените команду, чтобы соответствовать расположение и имя файла резервной копии.

   ```bash
   mv /home/user1/YourDB.bak /var/opt/mssql/backup/
   ```

1. Выход из режима суперпользователя.

   ```bash
   exit
   ```

## <a name="restore-your-database-on-linux"></a>Восстановить базу данных в Linux

Чтобы восстановить резервную копию базы данных, можно использовать **RESTORE DATABASE** команды Transact-SQL (TQL).

> [!NOTE]
> В следующих шагах используется **sqlcmd** средства. Если вы этого еще не установки средства SQL Server, в разделе [средства командной строки установки SQL Server в Linux](sql-server-linux-setup-tools.md).

1. В одном терминала, запустите **sqlcmd**. Следующий пример подключается к локальному экземпляру SQL Server с **SA** пользователя. Пароль при появлении запроса введите или укажите пароль, добавив **-P** параметра.

   ```bash
   sqlcmd -S localhost -U SA
   ```

1. В `>1` введите следующие **RESTORE DATABASE** команды, нажимая клавишу ВВОД после каждой строки (Невозможно скопировать и вставить вся команда несколько строк за один раз). Замените все вхождения `YourDB` с именем базы данных.

   ```sql
   RESTORE DATABASE YourDB
   FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   WITH MOVE 'YourDB' TO '/var/opt/mssql/data/YourDB.mdf',
   MOVE 'YourDB_Log' TO '/var/opt/mssql/data/YourDB_Log.ldf'
   GO
   ```

   Должно появиться сообщение, которое база данных успешно восстановлена.

1. Проверка восстановления, перечисляя все базы данных на сервере. Восстановленная база данных должна быть указана.

   ```sql
   SELECT Name FROM sys.Databases
   GO
   ```

1. Запустите другие запросы перенесенной базы данных. Следующая команда переключает контекст для **YourDB** базы данных и выбирает строки из одного из его таблиц.

   ```sql
   USE YourDB
   SELECT * FROM YourTable
   GO
   ```

1. После завершения с помощью **sqlcmd**, тип `exit`.

1. После завершения работы в удаленном **ssh** сеанса, введите `exit` еще раз.

## <a name="next-steps"></a>Следующие шаги

В этом учебнике вы узнали, как резервное копирование базы данных в Windows и переместите его на сервер Linux 2017 г. SQL Server. Узнать, как для:
> [!div class="checklist"]
> * Используйте SSMS и Transact-SQL для создания файла резервной копии в Windows
> * Установка оболочки Bash в Windows
> * Используйте **scp** для перемещения файлов резервной копии из Windows для Linux
> * Используйте **ssh** удаленно подключаться к компьютер Linux
> * Переместить файл резервной копии для подготовки к восстановлению
> * Используйте **sqlcmd** для выполнения команд Transact-SQL
> * Восстановите резервную копию базы данных с **RESTORE DATABASE** команды 

Затем исследовать другие сценарии миграции для SQL Server в Linux. 

> [!div class="nextstepaction"]
>[Перенос баз данных в SQL Server в Linux](sql-server-linux-migrate-overview.md)
