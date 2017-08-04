---
title: "Миграция базы данных SQL Server с Windows и Linux | Документы Microsoft"
description: "В этом разделе показано, как создать резервную копию базы данных SQL Server Windows и восстановите ее на компьютер Linux под управлением SQL Server, RC2 2017 г."
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9ac64d1a-9fe5-446e-93c3-d17b8f55a28f
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 2e23ba46381b1fb80b8ac335f6d7630f02a222bb
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restore"></a>Миграция базы данных SQL Server с Windows и Linux с помощью резервного копирования и восстановления

SQL Server резервного копирования, и функция восстановления рекомендуется использовать для миграции базы данных из SQL Server в Windows до RC2 2017 г. SQL Server в Linux. Этот раздел содержит пошаговые инструкции для этого метода. В этом учебнике рассматриваются следующие задачи:

- Загрузите файл резервной копии AdventureWorks на компьютере с ОС Windows
- Перенос резервного копирования на компьютер Linux
- Восстановите базу данных с помощью команды Transact-SQL

> [!NOTE] 
> В этом учебнике предполагается, что вы установили [RC2 2017 г. SQL Server](sql-server-linux-setup.md) и [средств SQL Server](sql-server-linux-setup-tools.md) на целевом сервере Linux.

## <a name="download-the-adventureworks-database-backup"></a>Загрузите резервной копии базы данных AdventureWorks

Несмотря на то, что можно использовать те же действия для восстановления любой базы данных, в базе данных AdventureWorks предоставляет хороший пример. Он поставляется в виде существующего файла резервной копии базы данных.

>[!NOTE] 
> Чтобы восстановить базу данных SQL Server в Linux, необходимо сделать резервную источника из SQL Server 2014 или SQL Server 2016. Резервное копирование SQL Server номер сборки не может быть больше, чем восстановление SQL Server номер сборки.  

1. На компьютере Windows, перейдите в раздел [https://msftdbprodsamples.codeplex.com/downloads/get/880661](https://msftdbprodsamples.codeplex.com/downloads/get/880661) и загрузите **Backup.zip полной базы данных Adventure Works 2014**.

   > [!TIP] 
   > Несмотря на то, что в этом учебнике показано резервного копирования и восстановления между Windows и Linux, можно также использовать браузер в Linux непосредственно загрузить образцы AdventureWorks на компьютер Linux.

2. Откройте ZIP-файл и извлеките файл AdventureWorks2014.bak в папку на компьютере.

## <a name="transfer-the-backup-file-to-linux"></a>Передача файла резервной копии в Linux

Чтобы восстановить базу данных, сначала следует перенести файл резервной копии на компьютере Windows на целевом компьютере Linux.

1. Для Windows установите оболочку Bash. Существует несколько параметров, включая следующие:

   - Загрузите открытой Bash оболочки, такие как [PuTTY](http://www.putty.org/).
   - Или, в Windows 10 используйте новую [встроенных команд Bash (бета-версия)](https://msdn.microsoft.com/en-us/commandline/wsl/about).
   - Если вы работаете с Git, используйте [Git Bash оболочки](https://git-scm.com/downloads).

2. Откройте оболочку Bash (терминалов) и перейдите в каталог, содержащий **AdventureWorks2014.bak**.

3. Используйте **scp** команду (безопасного копирования), чтобы переместить файл на целевом компьютере Linux. Следующий пример передачи **AdventureWorks2014.bak** для домашнего каталога *user1* на сервере с именем *linuxserver1*.

   ```bash
   sudo scp AdventureWorks2014.bak user1@linuxserver1:./
   ```
   
   В предыдущем примере можно вместо этого указать IP-адрес вместо имени сервера.

Существует несколько альтернативы использованию scp. Один является применение [Samba](https://help.ubuntu.com/community/Samba) для настройки сетевой папке SMB между Windows и Linux. Пошаговое руководство Ubuntu см. в разделе [Создание сетевой папки через Samba](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!). После установки, его можно получить в виде файла сети общую папку из Windows, таких как  **\\ \\machinenameorip\\совместное использование**.

## <a name="move-the-backup-file"></a>Перемещение файла резервной копии

В этот момент файл резервной копии находится на сервере Linux. Перед восстановлением базы данных в SQL Server, резервное копирование необходимо поместить в подкаталоге **/var/opt/mssql**.

1. Откройте терминал на целевом компьютере Linux с используемой резервной копией.

2. Перейдите в режим суперпользователя.

   ```bash
   sudo su
   ```

3. Создайте новый каталог резервного копирования. Если каталог уже существует, параметр -p не выполняет никаких действий.

   ```bash
   mkdir -p /var/opt/mssql/backup
   ```

4. Переместите файл резервной копии к этому каталогу. В следующем примере файл резервной копии находится в домашнем каталоге *user1*. Изменить команду, чтобы соответствовать расположение **AdventureWorks2014.bak** на компьютере.

   ```bash
   mv /home/user1/AdventureWorks2014.bak /var/opt/mssql/backup/
   ```

5. Выход из режима суперпользователя.

   ```bash
   exit
   ```

## <a name="restore-the-database-backup"></a>Восстановите резервную копию базы данных

Восстановление резервной копии, можно использовать команду RESTORE языка Transact-SQL базы данных (TQL).

> [!NOTE] 
> В следующих действиях используется средство sqlcmd. Если вы этого еще не установки средства SQL Server, в разделе [Установка SQL Server в Linux](sql-server-linux-setup.md).

1. В одном терминала, запустите **sqlcmd**. Следующий пример подключается к локальному экземпляру SQL Server с *SA* пользователя. Введите пароль, когда запрос или задайте с помощью параметра -P пароль.

   ```bash
   sqlcmd -S localhost -U SA
   ```

2. После подключения введите следующие **восстановления данных** команды, нажимая клавишу ВВОД после каждой строки. Пример ниже восстановление **AdventureWorks2014.bak** файл из */var/opt/mssql/backup* каталога.

   ```sql
   RESTORE DATABASE AdventureWorks
   FROM DISK = '/var/opt/mssql/backup/AdventureWorks2014.bak'
   WITH MOVE 'AdventureWorks2014_Data' TO '/var/opt/mssql/data/AdventureWorks2014_Data.mdf',
   MOVE 'AdventureWorks2014_Log' TO '/var/opt/mssql/data/AdventureWorks2014_Log.ldf'
   GO
   ```

   Должно появиться сообщение, которое база данных успешно восстановлена.

3. Проверка восстановления путем изменения контекста к базе данных AdventureWorks. 

   ```sql
   USE AdventureWorks
   GO
   ```

4. Выполните следующий запрос, содержащий 10 самых популярных продуктов в **Production.Products** таблицы.

   ```sql
   SELECT TOP 10 Name, ProductNumber FROM Production.Product ORDER BY Name
   GO
   ```

![Выходные данные из запроса Production.Products](./media/sql-server-linux-migrate-restore-database/sql-server-linux-adventureworks-query.png)

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других методов переноса базы данных и данных см. в разделе [переноса баз данных в SQL Server в Linux](sql-server-linux-migrate-overview.md). 

