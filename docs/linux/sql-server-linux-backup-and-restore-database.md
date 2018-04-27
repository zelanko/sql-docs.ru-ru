---
title: Резервное копирование и восстановление баз данных SQL Server в Linux | Документы Microsoft
description: Узнайте, как резервное копирование и восстановление баз данных SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 11/14/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: d30090fb-889f-466e-b793-5f284fccc4e6
ms.workload: On Demand
ms.openlocfilehash: e46a11d935b06f7b2d491c716aa6119dc08f19dd
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="backup-and-restore-sql-server-databases-on-linux"></a>Резервное копирование и восстановление баз данных SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Резервные копии баз данных может занять от 2017 г. SQL Server в Linux с помощью тех же средств, как другие платформы. На сервере Linux, можно использовать **sqlcmd** для подключения к SQL Server и создания резервных копий. В операционной системе Windows можно подключиться к SQL Server в Linux и резервных копий с помощью пользовательского интерфейса. Функциональные возможности резервного копирования является одинаковым для платформы. Например, можно сделать резервную копию баз данных локально, чтобы удаленные диски, а также к [службы хранилища больших двоичных объектов Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-to-url.md).

## <a name="backup-a-database"></a>Резервное копирование базы данных

В следующем примере **sqlcmd** подключается к локальному экземпляру SQL Server и принимает полной резервной копии пользовательской базы данных называется `demodb`.

```bash
sqlcmd -S localhost -U SA -Q "BACKUP DATABASE [demodb] TO DISK = N'/var/opt/mssql/data/demodb.bak' WITH NOFORMAT, NOINIT, NAME = 'demodb-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```

При выполнении команды SQL Server предложит ввести пароль. После ввода пароля оболочки возвратит результаты работы резервного копирования. Например:

```
Password:
10 percent processed.
21 percent processed.
32 percent processed.
40 percent processed.
51 percent processed.
61 percent processed.
72 percent processed.
80 percent processed.
91 percent processed.
Processed 296 pages for database 'demodb', file 'demodb' on file 1.
100 percent processed.
Processed 2 pages for database 'demodb', file 'demodb_log' on file 1.
BACKUP DATABASE successfully processed 298 pages in 0.064 seconds (36.376 MB/sec).
```

### <a name="backup-the-transaction-log"></a>Резервное копирование журнала транзакций

Если в модели полного восстановления базы данных, вы также можете резервных копий журналов транзакций для более детального параметры восстановления. В следующем примере **sqlcmd** подключается к локальному экземпляру SQL Server и принимает резервного копирования журнала транзакций.

```bash
sqlcmd -S localhost -U SA -Q "BACKUP LOG [demodb] TO DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak' WITH NOFORMAT, NOINIT, NAME = N'demodb_LogBackup', NOSKIP, NOREWIND, NOUNLOAD, STATS = 5"
```

## <a name="restore-a-database"></a>Восстановление базы данных

В следующем примере **sqlcmd** подключается к локальному экземпляру SQL Server и восстанавливает базу данных demodb. Обратите внимание, что `NORECOVERY` параметр используется для разрешения для дополнительных восстанавливает резервные копии файла журнала. Если вы не планируете восстановить дополнительные файлы журналов, удалите `NORECOVERY` параметр.

```bash
sqlcmd -S localhost -U SA -Q "RESTORE DATABASE [demodb] FROM DISK = N'/var/opt/mssql/data/demodb.bak' WITH FILE = 1, NOUNLOAD, REPLACE, NORECOVERY, STATS = 5"
```

> [!TIP]
> Если вы случайно, используйте параметр NORECOVERY, но нет дополнительных файлов резервных копий журнала, выполните команду `RESTORE DATABASE demodb` без дополнительных параметров. Это завершает восстановление и оставляет базу данных в состоянии.

### <a name="restore-the-transaction-log"></a>Восстановление журнала транзакций

Следующая команда восстанавливает предыдущей резервной копии журнала транзакций.

```bash
sqlcmd -S localhost -U SA -Q "RESTORE LOG demodb FROM DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak'"
```

## <a name="backup-and-restore-with-sql-server-management-studio-ssms"></a>Резервное копирование и восстановление с помощью SQL Server Management Studio (SSMS)

Среда SSMS с компьютера Windows можно использовать для подключения к базе данных Linux и резервное копирование через пользовательский интерфейс.

>[!NOTE] 
> Используйте последнюю версию SSMS для подключения к SQL Server. Чтобы загрузить и установить последнюю версию, в разделе [загрузки SSMS](../ssms/download-sql-server-management-studio-ssms.md). Дополнительные сведения о том, как с помощью среды SSMS см. в разделе [используйте SSMS для управления SQL Server в Linux](sql-server-linux-manage-ssms.md).

Ниже приведены шаги Создание резервной копии с помощью SSMS. 

1. Запустите SSMS и подключитесь к серверу в 2017 г. SQL Server в Linux.

1. В обозревателе объектов щелкните правой кнопкой базу данных, нажмите кнопку **задачи**, а затем нажмите кнопку **создайте резервную копию...** .

1. В **резервное копирование копии базы данных** диалогового окна, проверьте параметры и параметры и нажмите кнопку **ОК**.
 
SQL Server завершает резервной копии базы данных.

### <a name="restore-with-sql-server-management-studio-ssms"></a>Восстановление с SQL Server Management Studio (SSMS) 

Следующие шаги описывают восстановление базы данных с помощью SSMS.

1. В среде SSMS щелкните правой кнопкой мыши **баз данных** и нажмите кнопку **восстановление баз данных...** . 

1. В разделе **источника** щелкните **устройства:** и нажмите кнопку с многоточием (...).

1. Найдите файл резервной копии базы данных и нажмите кнопку **ОК**. 

1. В разделе **план восстановления**, проверьте файл резервной копии и параметры. Нажмите кнопку **ОК**. 

1. SQL Server восстанавливает базу данных. 

## <a name="see-also"></a>См. также:

* [Создание полной резервной копии (SQL Server)](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)
* [Резервное копирование журнала транзакций (SQL Server)](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)
* [BACKUP (Transact-SQL)](../t-sql/statements/backup-transact-sql.md)
* [Резервное копирование в SQL Server по URL-адресу](../relational-databases/backup-restore/sql-server-backup-to-url.md)
