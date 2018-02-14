---
title: "Приостановка и возобновление переноса данных (Stretch Database) | Документация Майкрософт"
ms.custom: 
ms.date: 06/14/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: stretch-database
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, pausing and resuming
- pausing Stretch Database
- resuming Stretch Database
ms.assetid: 65d6a990-b295-41b2-97f9-7b6bf3000e4d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1a668af6406490e36584d9ad7754f4f783b8b0be
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="pause-and-resume-data-migration-stretch-database"></a>Приостановка и возобновление переноса данных (Stretch Database)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


  Чтобы приостановить или возобновить перенос данных в Azure, выберите **Stretch** в качестве таблицы в SQL Server Management Studio, а затем — команду **Приостановить** , чтобы приостановить перенос данных, или **Возобновить** , чтобы возобновить его. Эти действия можно также выполнить с помощью Transact-SQL.  
  
 Вы можете приостановить перенос данных в отдельных таблицах для устранения неполадок на локальном сервере или увеличения доступной пропускной способности сети.  

## <a name="pause-data-migration"></a>Приостановка переноса данных  
  
### <a name="use-sql-server-management-studio-to-pause-data-migration"></a>Остановка переноса данных с помощью SQL Server Management Studio  
  
1.  В среде SQL Server Management Studio в обозревателе объектов выберите таблицу с поддержкой Stretch, для которой нужно приостановить перенос данных.  
  
2.  Щелкните таблицу правой кнопкой мыши и выберите **Stretch**, а затем **Приостановить**.  
  
### <a name="use-transact-sql-to-pause-data-migration"></a>Остановка переноса данных с помощью Transact-SQL  
 Выполните следующую команду.  
  
```sql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>  
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = PAUSED ) ) ;  
GO 
```  
  
## <a name="resume-data-migration"></a>Возобновление переноса данных  
  
### <a name="use-sql-server-management-studio-to-resume-data-migration"></a>Возобновление переноса данных с помощью SQL Server Management Studio  
  
1.  В среде SQL Server Management Studio в обозревателе объектов выберите таблицу с поддержкой Stretch, для которой нужно возобновить перенос данных.  
  
2.  Щелкните таблицу правой кнопкой мыши и выберите **Stretch**, а затем **Возобновить**.  
  
### <a name="use-transact-sql-to-resume-data-migration"></a>Возобновление переноса данных с помощью Transact-SQL  
 Выполните следующую команду.  
  
```sql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>   
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = OUTBOUND ) ) ;  
 GO
```  

## <a name="check-whether-migration-is-active-or-paused"></a>Проверьте, активна миграция или приостановлена

### <a name="use-sql-server-management-studio-to-check-whether-migration-is-active-or-paused"></a>С помощью среды SQL Server Management Studio проверьте, активна миграция или приостановлена.
В SQL Server Management Studio откройте **монитор Stretch Database** и проверьте значение в столбце **Состояние миграции** . Дополнительные сведения см. в статье [Мониторинг переноса данных и устранение неполадок](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).

### <a name="use-transact-sql-to-check-whether-migration-is-active-or-paused"></a>С помощью Transact-SQL проверьте, активна миграция или приостановлена.
Запросите представление каталога **sys.remote_data_archive_tables** и проверьте значение в столбце **is_migration_paused** . Дополнительные сведения см. в разделе [sys.remote_data_archive_tables](../../relational-databases/system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-tables.md).

## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Мониторинг переноса данных и устранение неполадок](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md) 
  
