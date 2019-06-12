---
title: Краткое руководство. Локальное резервное копирование и восстановление баз данных SQL Server
titleSuffix: SQL Server
description: В этом кратком руководстве показано, как запустить SQL Server на Linux в облаке по своему усмотрению.
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.date: 05/25/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: ''
ms.technology: backup-restore
ms.prod_service: backup-restore
ms.assetid: ''
ms.openlocfilehash: 8453d74227e1007a42adfbd8ac1f91bf1a6d86da
ms.sourcegitcommit: 1800fc15075bb17b50d0c18b089d8a64d87ae726
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66499670"
---
# <a name="quickstart-backup-and-restore-a-sql-server-database-on-premises"></a>Краткое руководство. Локальное резервное копирование и восстановление баз данных SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве нам предстоит создать новую базу данных, выполнить простое резервное копирование и затем восстановить ее. 

Более подробные инструкции см. в разделе [Создание полной резервной копии базы данных](create-a-full-database-backup-sql-server.md) и [Восстановление резервной копии с помощью среды SSMS](restore-a-database-backup-using-ssms.md).

## <a name="prerequisites"></a>предварительные требования
Для работы с этим кратким руководством вам потребуется следующее: 

- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md)

## <a name="create-a-test-database"></a>Создание тестовой базы данных 

1. Запустите среду [SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md) и подключитесь к своему экземпляру SQL Server.
1. Откройте окно **Новый запрос**. 
1. Выполните следующий код Transact-SQL (T-SQL) для создания тестовой базы данных. Обновите узел **Базы данных** в **обозревателе объектов** для отображения новой базы данных. 

```sql
USE [master]
GO

CREATE DATABASE [SQLTestDB]
GO

USE [SQLTestDB]
GO
CREATE TABLE SQLTest (
    ID INT NOT NULL PRIMARY KEY,
    c1 VARCHAR(100) NOT NULL,
    dt1 DATETIME NOT NULL DEFAULT getdate()
)
GO


USE [SQLTestDB]
GO

INSERT INTO SQLTest (ID, c1) VALUES (1, 'test1')
INSERT INTO SQLTest (ID, c1) VALUES (2, 'test2')
INSERT INTO SQLTest (ID, c1) VALUES (3, 'test3')
INSERT INTO SQLTest (ID, c1) VALUES (4, 'test4')
INSERT INTO SQLTest (ID, c1) VALUES (5, 'test5')
GO

SELECT * FROM SQLTest
GO
```
 
## <a name="take-a-backup"></a>Создание резервной копии
Чтобы создать резервную копию базы данных, сделайте следующее. 

1. Запустите среду [SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md) и подключитесь к своему экземпляру SQL Server.
1. В **обозревателе объектов** разверните узел **Базы данных**.  
1. Щелкните правой кнопкой мыши базу данных, наведите указатель мыши на **Задачи**и выберите **Резервное копирование...** . 
1. В разделе **Назначение** проверьте путь к резервной копии. Если вам нужно изменить его, выберите **Удалить**, чтобы удалить существующий путь, а затем **Добавить**, чтобы ввести новый путь. Можно использовать кнопку с многоточием для перехода к определенному файлу. 
1. Чтобы создать резервную копию базы данных, нажмите **ОК**. 

![Создание резервной копии SQL](media/quickstart-backup-restore-database/backup-db-ssms.png)

Кроме того, можно выполнить следующую команду Transact-SQL для резервного копирования базы данных: 

```sql
BACKUP DATABASE [SQLTestDB] 
TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Backup\SQLTestDB.bak' 
WITH NOFORMAT, NOINIT,  
NAME = N'SQLTestDB-Full Database Backup', SKIP, NOREWIND, NOUNLOAD,  STATS = 10
GO
```


## <a name="restore-a-backup"></a>Восстановление резервной копии
Для восстановления базы данных выполните следующие действия. 

1. Запустите среду [SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md) и подключитесь к своему экземпляру SQL Server.
1. Щелкните правой кнопкой мыши узел **Базы данных** в **обозревателе объектов** и выберите **Восстановить базу данных...** .

    ![Восстановление базы данных](media/quickstart-backup-restore-database/restore-db-ssms1.png)

1. Выберите **Устройство:** и нажмите кнопку с многоточием (...), чтобы найти файл резервной копии. 
1. Выберите **Добавить** и перейдите в расположение вашего файла `.bak`. Выберите файл `.bak` и затем нажмите **ОК**. 
1. Снова нажмите **ОК** в диалоговом окне **Выбор устройств резервного копирования**, чтобы закрыть его. 
1. Чтобы восстановить резервную копию базы данных, нажмите **ОК**. 

    ![Восстановление базы данных](media/quickstart-backup-restore-database/restore-db-ssms2.png)

Кроме того, можно выполнить следующий скрипт Transact-SQL для восстановления базы данных:

```sql
USE [master]
RESTORE DATABASE [SQLTestDB] 
FROM DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Backup\SQLTestDB.bak' WITH  FILE = 1,  NOUNLOAD,  STATS = 5
GO
```

### <a name="clean-up-resources"></a>Очистка ресурсов
Выполните следующую команду Transact-SQL, чтобы удалить базу данных, которую вы создали, а также свой журнал резервного копирования в базе данных MSDB:

```sql
EXEC msdb.dbo.sp_delete_database_backuphistory @database_name = N'SQLTestDB'
GO

USE [master]
DROP DATABASE [SQLTestDB]
GO
```

## <a name="see-more"></a>Подробнее
[Резервное копирование и восстановление — обзор](back-up-and-restore-of-sql-server-databases.md)
[Резервное копирование на URL-адрес](sql-server-backup-to-url.md)
[Создание полной резервной копии](create-a-full-database-backup-sql-server.md)
[Восстановление резервной копии базы данных](restore-a-database-backup-using-ssms.md)
