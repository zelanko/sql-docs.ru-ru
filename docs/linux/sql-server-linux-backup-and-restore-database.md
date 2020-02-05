---
title: Резервное копирование и восстановление баз данных SQL Server в Linux
description: Сведения о резервном копировании и восстановлении баз данных SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 11/14/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: d30090fb-889f-466e-b793-5f284fccc4e6
ms.openlocfilehash: 88ef620a24bc2ce623ea6fb072871dadeffbcf6d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68823111"
---
# <a name="backup-and-restore-sql-server-databases-on-linux"></a>Резервное копирование и восстановление баз данных SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Вы можете создавать резервные копии баз данных из SQL Server 2017 в Linux различными способами. На сервере Linux можно использовать **sqlcmd** для подключения к SQL Server и создания резервных копий. Из Windows можно подключиться к SQL Server в Linux и создать резервные копии с помощью пользовательского интерфейса. Функция резервного копирования одинакова для разных платформ. Например, можно выполнять резервное копирование баз данных локально, на удаленные диски или в [службу хранилища BLOB-объектов Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-to-url.md).

## <a name="backup-a-database"></a>Резервное копирование базы данных

В следующем примере **sqlcmd** подключается к локальному экземпляру SQL Server и создает полную резервную копию пользовательской базы данных `demodb`.

```bash
sqlcmd -S localhost -U SA -Q "BACKUP DATABASE [demodb] TO DISK = N'/var/opt/mssql/data/demodb.bak' WITH NOFORMAT, NOINIT, NAME = 'demodb-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```

При выполнении команды SQL Server запросит пароль. После ввода пароля оболочка возвратит результаты выполнения резервного копирования. Пример:

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

Если база данных находится в модели полного восстановления, то можно также создать резервные копии журналов транзакций для получения более детальных вариантов восстановления. В следующем примере **sqlcmd** подключается к локальному экземпляру SQL Server и создает резервную копию журнала транзакций.

```bash
sqlcmd -S localhost -U SA -Q "BACKUP LOG [demodb] TO DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak' WITH NOFORMAT, NOINIT, NAME = N'demodb_LogBackup', NOSKIP, NOREWIND, NOUNLOAD, STATS = 5"
```

## <a name="restore-a-database"></a>Восстановление базы данных

В следующем примере **sqlcmd** подключается к локальному экземпляру SQL Server и восстанавливает базу данных demodb. Обратите внимание на то, что используется параметр `NORECOVERY` для обеспечения дополнительного восстановления резервных копий файлов журнала. Если вы не планируете восстанавливать дополнительные файлы журналов, удалите параметр `NORECOVERY`.

```bash
sqlcmd -S localhost -U SA -Q "RESTORE DATABASE [demodb] FROM DISK = N'/var/opt/mssql/data/demodb.bak' WITH FILE = 1, NOUNLOAD, REPLACE, NORECOVERY, STATS = 5"
```

> [!TIP]
> Если вы случайно используете параметр NORECOVERY, но у вас нет дополнительных резервных копий файлов журнала, выполните команду `RESTORE DATABASE demodb` без дополнительных параметров. При этом восстановление завершается, а база данных остается в рабочем состоянии.

### <a name="restore-the-transaction-log"></a>Восстановление журнала транзакций

Следующая команда восстанавливает предыдущую резервную копию журнала транзакций.

```bash
sqlcmd -S localhost -U SA -Q "RESTORE LOG demodb FROM DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak'"
```

## <a name="backup-and-restore-with-sql-server-management-studio-ssms"></a>Резервное копирование и восстановление с помощью SQL Server Management Studio (SSMS)

Среду SSMS можно использовать с компьютера Windows для подключения к базе данных Linux и резервного копирования через пользовательский интерфейс.

>[!NOTE] 
> Используйте последнюю версию SSMS для подключения к SQL Server. Чтобы скачать и установить последнюю версию, см. статью [Скачивание SSMS](../ssms/download-sql-server-management-studio-ssms.md). Дополнительные сведения об использовании SSMS см. в статье [Управление SQL Server на Linux с помощью SSMS](sql-server-linux-manage-ssms.md).

Ниже приведены пошаговые инструкции по резервному копированию с помощью SSMS. 

1. Запустите SSMS и подключитесь к серверу в SQL Server 2017 в Linux.

1. В обозревателе объектов щелкните правой кнопкой мыши базу данных, выберите пункт **Задачи** и затем **Создать резервную копию...**

1. Проверьте параметры в диалоговом окне **Резервное копирование базы данных** и нажмите кнопку **ОК**.
 
SQL Server завершает резервное копирование базы данных.

### <a name="restore-with-sql-server-management-studio-ssms"></a>Восстановление с помощью SQL Server Management Studio (SSMS) 

Ниже приведены пошаговые инструкции по восстановлению базы данных с помощью SSMS.

1. В SSMS щелкните правой кнопкой мыши элемент **Базы данных** и выберите пункт **Восстановить базы данных...** 

1. В разделе **Источник** щелкните **Устройство:** и многоточие (...).

1. Выберите файл резервной копии базы данных и нажмите кнопку **ОК**. 

1. В разделе **План восстановления** проверьте параметры и файл резервной копии. Нажмите кнопку **ОК**. 

1. SQL Server восстанавливает базу данных. 

## <a name="see-also"></a>См. также раздел

* [Создание полной резервной копии базы данных (SQL Server)](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)
* [Создание резервной копии журнала транзакций (SQL Server)](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)
* [BACKUP (Transact-SQL)](../t-sql/statements/backup-transact-sql.md)
* [Резервное копирование SQL Server в указанное расположение](../relational-databases/backup-restore/sql-server-backup-to-url.md).
