---
title: Резервное копирование и восстановление баз данных SQL Server в Linux | Документация Майкрософт
description: Узнайте, как резервное копирование и восстановление баз данных SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 11/14/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: d30090fb-889f-466e-b793-5f284fccc4e6
ms.openlocfilehash: 707801b47258d48661a4f0725c2ee7062b1a40a0
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086557"
---
# <a name="backup-and-restore-sql-server-databases-on-linux"></a>Резервное копирование и восстановление баз данных SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Можно создавать резервные копии баз данных из SQL Server 2017 в Linux с помощью тех же средств, как другие платформы. На сервере Linux, можно использовать **sqlcmd** для подключения к SQL Server и создавать резервные копии. Из Windows можно подключиться к SQL Server в Linux и создавать резервные копии с пользовательским интерфейсом. Функциональные возможности резервного копирования является одинаковым для платформ. Например, можно выполнить резервное копирование баз данных локально, чтобы удаленные диски или к [службы хранилища больших двоичных объектов Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-to-url.md).

## <a name="backup-a-database"></a>Резервное копирование базы данных

В следующем примере **sqlcmd** подключается к локальному экземпляру SQL Server и принимает полной резервной копии пользовательской базы данных называется `demodb`.

```bash
sqlcmd -S localhost -U SA -Q "BACKUP DATABASE [demodb] TO DISK = N'/var/opt/mssql/data/demodb.bak' WITH NOFORMAT, NOINIT, NAME = 'demodb-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```

При выполнении команды SQL Server предложит ввести пароль. После того как вы введете пароль, оболочка вернет результаты работы резервного копирования. Пример:

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

Если база данных в модели полного восстановления, вы также можете резервные копии журналов транзакций для более детализированные параметры восстановления. В следующем примере **sqlcmd** подключается к локальному экземпляру SQL Server и принимает резервного копирования журнала транзакций.

```bash
sqlcmd -S localhost -U SA -Q "BACKUP LOG [demodb] TO DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak' WITH NOFORMAT, NOINIT, NAME = N'demodb_LogBackup', NOSKIP, NOREWIND, NOUNLOAD, STATS = 5"
```

## <a name="restore-a-database"></a>Восстановление базы данных

В следующем примере **sqlcmd** подключается к локальному экземпляру SQL Server и восстанавливает базу данных demodb. Обратите внимание, что `NORECOVERY` параметр используется для разрешения для дополнительных операций восстановления из резервных копий файла журнала. Если вы не планируете восстановить дополнительные файлы журналов, удалите `NORECOVERY` параметр.

```bash
sqlcmd -S localhost -U SA -Q "RESTORE DATABASE [demodb] FROM DISK = N'/var/opt/mssql/data/demodb.bak' WITH FILE = 1, NOUNLOAD, REPLACE, NORECOVERY, STATS = 5"
```

> [!TIP]
> Если вы случайно инструкции WITH NORECOVERY, но не имеют дополнительный журнал резервных копий файлов, выполните команду `RESTORE DATABASE demodb` без дополнительных параметров. Это завершает восстановление и оставляет базу данных оперативной.

### <a name="restore-the-transaction-log"></a>Восстановление журнала транзакций

Следующая команда восстанавливает предыдущей резервной копии журнала транзакций.

```bash
sqlcmd -S localhost -U SA -Q "RESTORE LOG demodb FROM DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak'"
```

## <a name="backup-and-restore-with-sql-server-management-studio-ssms"></a>Резервное копирование и восстановление с помощью SQL Server Management Studio (SSMS)

SSMS с компьютера Windows, можно использовать для соединения с базой данных Linux и выполнить резервное копирование через интерфейс пользователя.

>[!NOTE] 
> Используйте последнюю версию SSMS для подключения к SQL Server. Чтобы загрузить и установить последнюю версию, см. в разделе [скачивание SSMS](../ssms/download-sql-server-management-studio-ssms.md). Дополнительные сведения о том, как использовать SSMS см. в разделе [использовать SSMS для управления SQL Server в Linux](sql-server-linux-manage-ssms.md).

Ниже приведены инструкции по Создание резервной копии с помощью SSMS. 

1. Запустите SSMS и подключитесь к серверу в SQL Server 2017 в Linux.

1. В обозревателе объектов щелкните правой кнопкой базу данных, нажмите кнопку **задачи**, а затем нажмите кнопку **резервного копирования...** .

1. В **резервной копии базы данных** диалоговое окно, проверьте параметры и параметры и нажмите кнопку **ОК**.
 
SQL Server завершает резервной копии базы данных.

### <a name="restore-with-sql-server-management-studio-ssms"></a>Восстановление с помощью SQL Server Management Studio (SSMS) 

Ниже приведены пошаговые восстановление базы данных с помощью SSMS.

1. В среде SSMS щелкните правой кнопкой мыши **баз данных** и нажмите кнопку **восстановление баз данных...** . 

1. В разделе **источника** щелкните **устройства:** и нажмите кнопку с многоточием (...).

1. Найдите файл резервной копии базы данных и нажмите кнопку **ОК**. 

1. В разделе **план восстановления**, проверьте файл резервной копии и параметры. Нажмите кнопку **ОК**. 

1. SQL Server восстанавливает базу данных. 

## <a name="see-also"></a>См. также

* [Создание полной резервной копии (SQL Server)](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)
* [Резервное копирование журнала транзакций (SQL Server)](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)
* [BACKUP (Transact-SQL)](../t-sql/statements/backup-transact-sql.md)
* [Резервное копирование в SQL Server по URL-адресу](../relational-databases/backup-restore/sql-server-backup-to-url.md)
