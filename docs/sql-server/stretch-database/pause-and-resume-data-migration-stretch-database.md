---
title: "Приостановка и возобновление переноса данных (база данных Stretch) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/14/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "база данных Stretch, приостановка и возобновление"
  - "приостановка работы базы данных Stretch"
  - "возобновление работы базы данных Stretch"
ms.assetid: 65d6a990-b295-41b2-97f9-7b6bf3000e4d
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Приостановка и возобновление переноса данных (база данных Stretch)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Чтобы приостановить или возобновить перенос данных в Azure, выберите **Stretch** в качестве таблицы в SQL Server Management Studio, а затем — команду **Приостановить**, чтобы приостановить перенос данных, или **Возобновить**, чтобы возобновить его. Эти действия можно также выполнить с помощью Transact-SQL.  
  
 Вы можете приостановить перенос данных в отдельных таблицах для устранения неполадок на локальном сервере или увеличения доступной пропускной способности сети.  

## Приостановка переноса данных  
  
### Остановка переноса данных с помощью SQL Server Management Studio  
  
1.  В среде SQL Server Management Studio в обозревателе объектов выберите таблицу с поддержкой Stretch, для которой нужно приостановить перенос данных.  
  
2.  Щелкните таблицу правой кнопкой мыши и выберите **Stretch**, а затем **Приостановить**.  
  
### Остановка переноса данных с помощью Transact-SQL  
 Выполните следующую команду.  
  
```tsql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>  
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = PAUSED ) ) ;  
GO 
```  
  
## Возобновление переноса данных  
  
### Возобновление переноса данных с помощью SQL Server Management Studio  
  
1.  В среде SQL Server Management Studio в обозревателе объектов выберите таблицу с поддержкой Stretch, для которой нужно возобновить перенос данных.  
  
2.  Щелкните таблицу правой кнопкой мыши и выберите **Stretch**, а затем **Возобновить**.  
  
### Возобновление переноса данных с помощью Transact-SQL  
 Выполните следующую команду.  
  
```tsql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>   
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = OUTBOUND ) ) ;  
 GO
```  

## Проверьте, активна миграция или приостановлена

### С помощью среды SQL Server Management Studio проверьте, активна миграция или приостановлена.
В SQL Server Management Studio откройте **монитор базы данных Stretch** и проверьте значение в столбце **Состояние миграции**. Дополнительные сведения см. в статье [Мониторинг переноса данных и устранение неполадок](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).

### С помощью Transact-SQL проверьте, активна миграция или приостановлена.
Запросите представление каталога **sys.remote_data_archive_tables** и проверьте значение в столбце **is_migration_paused**. Дополнительные сведения см. в разделе [sys.remote_data_archive_tables](sys.remote_data_archive_tables%20\(Transact-SQL\).md).

## См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Мониторинг переноса данных и устранение неполадок](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md) 
  