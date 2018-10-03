---
title: Перенос базы данных SQL Server из Windows для Linux | Документация Майкрософт
description: Этом руководстве показано, как создать резервную копию базы данных SQL Server на Windows и восстановить ее на компьютер Linux под управлением SQL Server.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/16/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 9ac64d1a-9fe5-446e-93c3-d17b8f55a28f
ms.openlocfilehash: 0da1e0c866d0934671ebe6291c39d2247a28de07
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729422"
---
# <a name="migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restore"></a>Перенос базы данных SQL Server из Windows для Linux с помощью резервного копирования и восстановления

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server для резервного копирования и функция восстановления рекомендуется использовать для переноса базы данных из SQL Server в Windows для SQL Server в Linux. В этом руководстве приведены пошаговые инструкции описаны действия, необходимые для перемещения базы данных Linux с помощью службы архивации и восстановления методы.

> [!div class="checklist"]
> * Создание файла резервной копии в Windows с помощью SSMS
> * Установка оболочки Bash в Windows
> * Перемещение файла резервной копии для Linux из оболочки Bash
> * Восстановить файл резервной копии на платформе Linux с помощью Transact-SQL
> * Выполните запрос, чтобы проверка миграции

Можно также создать SQL Server всегда группу доступности для переноса базы данных SQL Server из Windows в Linux. См. в разделе [sql-server-linux-availability-group-cross-platform](sql-server-linux-availability-group-cross-platform.md).

## <a name="prerequisites"></a>предварительные требования

Для работы с этим руководством требуются следующие компоненты:

* Компьютер Windows со следующими:
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions) установлен.
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) установлен.
  * Целевая база данных для миграции.

* Компьютер Linux установлены следующие компоненты:
  * SQL Server ([RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), или [Ubuntu](quickstart-install-connect-ubuntu.md)) с помощью средства командной строки.

## <a name="create-a-backup-on-windows"></a>Создание резервной копии в Windows

Существует несколько способов создания файла резервной копии базы данных на Windows. Далее используется SQL Server Management Studio (SSMS).

1. Запуск **SQL Server Management Studio** на компьютере Windows.

1. В диалоговом окне соединения введите **localhost**.

1. В обозревателе объектов разверните **баз данных**.

1. Щелкните правой кнопкой мыши целевой базы данных, выберите **задачи**, а затем нажмите кнопку **резервного копирования...** .

   ![Создание файла резервной копии с помощью среды SSMS](./media/sql-server-linux-migrate-restore-database/ssms-create-backup.png)

1. В **резервной копии базы данных** диалоговое окно, убедитесь, что **тип резервной копии** — **полный** и **резервное копирование в** является **диска**. Обратите внимание на то, имя и расположение файла. Например, базу данных с именем **YourDB** на SQL Server 2016 имеет путь резервного копирования по умолчанию из `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak`.

1. Нажмите кнопку **ОК** для резервного копирования базы данных.

> [!NOTE]
> Другой вариант — выполнить запрос Transact-SQL для создания файла резервной копии. Следующую команду Transact-SQL выполняет те же действия, что ранее для базы данных называется **YourDB**:
>
> ```sql
> BACKUP DATABASE [YourDB] TO  DISK =
> N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak'
> WITH NOFORMAT, NOINIT, NAME = N'YourDB-Full Database Backup',
> SKIP, NOREWIND, NOUNLOAD, STATS = 10
> GO
> ```

## <a name="install-a-bash-shell-on-windows"></a>Установка оболочки Bash в Windows

Восстановление базы данных, сначала следует перенести файл резервной копии с компьютера Windows на целевой компьютер Linux. В этом руководстве мы переместите файл в Linux из оболочки Bash (окно терминала) под управлением Windows.

1. Установить оболочку Bash на компьютере Windows, которая поддерживает **scp** (secure копирования) и **ssh** команд (удаленный вход). Две следующие примеры.

   * [Подсистема Windows для Linux](https://msdn.microsoft.com/commandline/wsl/about) (Windows 10)
   * Оболочка Git Bash ([https://git-scm.com/downloads](https://git-scm.com/downloads))

1. Откройте сеанс Bash в Windows.

## <a id="scp"></a> Скопируйте файл резервной копии для Linux

1. В сеансе Bash перейдите к каталогу, содержащему файл архива. Пример:

   ```bash
   cd 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\'
   ```

1. Используйте **scp** команду, чтобы передать файл на целевой компьютер Linux. Следующий пример передачи **YourDB.bak** основной каталог *user1* на сервере Linux с помощью IP-адрес *192.0.2.9*:

   ```bash
   scp YourDB.bak user1@192.0.2.9:./
   ```
   ![команды scp](./media/sql-server-linux-migrate-restore-database/scp-command.png)

> [!TIP]
> Существуют альтернативы использованию scp для передачи файлов. Одним является использование [Samba](https://help.ubuntu.com/community/Samba) для настройки сетевой папке SMB между Windows и Linux. Пошаговое руководство по Ubuntu, см. в разделе [создании сетевой общей папки с помощью Samba](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!). После установки, его можно получить в виде файла сети общих из Windows, такие как  **\\ \\machinenameorip\\совместно использовать**.

## <a name="move-the-backup-file-before-restoring"></a>Перемещение файла резервной копии перед восстановлением

На этом этапе файл резервной копии находится на сервере Linux в домашнем каталоге пользователя. Перед восстановлением базы данных в SQL Server, необходимо разместить в подкаталоге каталога резервного копирования **/var/opt/mssql**.

1. В одном сеансе Windows Bash, удаленного подключения на целевом компьютере Linux с помощью **ssh**. Следующий пример подключается к компьютеру Linux **192.0.2.9** от имени пользователя **user1**.

   ```bash
   ssh user1@192.0.2.9
   ```

   Теперь вы выполняете команды на удаленном сервере Linux.

1. Перейти в режим суперпользователя.

   ```bash
   sudo su
   ```

1. Создайте новый каталог резервного копирования. Если каталог уже существует, параметр -p не выполняет никаких действий.

   ```bash
   mkdir -p /var/opt/mssql/backup
   ```

1. Переместите файл резервной копии в этот каталог. В следующем примере файл резервной копии находится в домашнем каталоге *user1*. Измените команду, чтобы соответствовать расположение и имя файла резервной копии.

   ```bash
   mv /home/user1/YourDB.bak /var/opt/mssql/backup/
   ```

1. Выйти из режима суперпользователя.

   ```bash
   exit
   ```

## <a name="restore-your-database-on-linux"></a>Восстановить базу данных на платформе Linux

Для восстановления резервной копии базы данных, можно использовать **RESTORE DATABASE** команды Transact-SQL (TQL).

> [!NOTE]
> В следующих действиях используется **sqlcmd** средство. Если вы этого еще не установить средства SQL Server, см. в разделе [средства командной строки установки SQL Server в Linux](sql-server-linux-setup-tools.md).

1. В том же окне терминала запустите **sqlcmd**. Следующий пример подключается к локальному экземпляру SQL Server с **SA** пользователя. Введите пароль при появлении запроса или указать пароль, добавив **-P** параметра.

   ```bash
   sqlcmd -S localhost -U SA
   ```

1. В `>1` введите следующие **RESTORE DATABASE** команды, нажимая клавишу ВВОД после каждой строки (Невозможно скопировать и вставить команду всего несколько строк за один раз). Замените все вхождения `YourDB` с именем базы данных.

   ```sql
   RESTORE DATABASE YourDB
   FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   WITH MOVE 'YourDB' TO '/var/opt/mssql/data/YourDB.mdf',
   MOVE 'YourDB_Log' TO '/var/opt/mssql/data/YourDB_Log.ldf'
   GO
   ```

   Должно появиться сообщение, которое база данных успешно восстановлена.

   `RESTORE DATABASE` могут возвращать ошибку, как в следующем примере:

   ```bash
   File 'YourDB_Product' cannot be restored to 'Z:\Microsoft SQL Server\MSSQL11.GLOBAL\MSSQL\Data\YourDB\YourDB_Product.ndf'. Use WITH MOVE to identify a valid location for the file.
   Msg 5133, Level 16, State 1, Server servername, Line 1
   Directory lookup for the file "Z:\Microsoft SQL Server\MSSQL11.GLOBAL\MSSQL\Data\YourDB\YourDB_Product.ndf" failed with the operating system error 2(The system cannot find the file specified.).
   ```
   
   В этом случае база данных содержит вторичных файлов. Если эти файлы не указаны в `MOVE` предложении `RESTORE DATABASE`, процедура восстановления будет пытаться создать их в тот же путь, что и исходный сервер. 

   Список всех файлов, включенных в резервную копию можно:
   ```sql
   RESTORE FILELISTONLY FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   GO
   ```
   Должен отобразиться список, подобный приведенному ниже (список только два первых столбцов).
   ```sql
   LogicalName         PhysicalName                                                                 ..............
   ----------------------------------------------------------------------------------------------------------------------
   YourDB              Z:\Microsoft SQL Server\MSSQL11.GLOBAL\MSSQL\Data\YourDB\YourDB.mdf          ..............
   YourDB_Product      Z:\Microsoft SQL Server\MSSQL11.GLOBAL\MSSQL\Data\YourDB\YourDB_Product.ndf  ..............
   YourDB_Customer     Z:\Microsoft SQL Server\MSSQL11.GLOBAL\MSSQL\Data\YourDB\YourDB_Customer.ndf ..............
   YourDB_log          Z:\Microsoft SQL Server\MSSQL11.GLOBAL\MSSQL\Data\YourDB\YourDB_Log.ldf      ..............
   ```
   
   Этот список можно использовать для создания `MOVE` предложения для дополнительных файлов. В этом примере `RESTORE DATABASE` является:

   ```sql
   RESTORE DATABASE YourDB
   FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   WITH MOVE 'YourDB' TO '/var/opt/mssql/data/YourDB.mdf',
   MOVE 'YourDB_Product' TO '/var/opt/mssql/data/YourDB_Product.ndf',
   MOVE 'YourDB_Customer' TO '/var/opt/mssql/data/YourDB_Customer.ndf',
   MOVE 'YourDB_Log' TO '/var/opt/mssql/data/YourDB_Log.ldf'
   GO
   ```


1. Проверка восстановления, перечисляя все базы данных на сервере. Восстановленная база данных должна быть указана.

   ```sql
   SELECT Name FROM sys.Databases
   GO
   ```

1. Запустите другие запросы перенесенной базы данных. Следующая команда изменяет контекст **YourDB** базы данных и выбирает строки из одной из его таблиц.

   ```sql
   USE YourDB
   SELECT * FROM YourTable
   GO
   ```

1. После завершения с помощью **sqlcmd**, тип `exit`.

1. После завершения работы в удаленном **ssh** сеанса, тип `exit` еще раз.

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как резервное копирование базы данных на Windows и переместите его на сервер Linux, под управлением SQL Server. Вы узнали, как для:
> [!div class="checklist"]
> * Использование SSMS и Transact-SQL для создания файла резервной копии в Windows
> * Установка оболочки Bash в Windows
> * Используйте **scp** для перемещения файлов резервных копий из Windows в Linux
> * Используйте **ssh** для удаленного подключения на компьютер Linux
> * Переместить файл резервной копии для подготовки к восстановлению
> * Используйте **sqlcmd** для выполнения команд Transact-SQL
> * Восстановите резервную копию базы данных с помощью **RESTORE DATABASE** команды 
> * Выполните запрос, чтобы проверка миграции

Затем изучите другие сценарии миграции для SQL Server в Linux. 

> [!div class="nextstepaction"]
>[Перенос баз данных в SQL Server в Linux](sql-server-linux-migrate-overview.md)
