---
description: Приостановка и возобновление переноса данных (Stretch Database)
title: Приостановка и возобновление переноса данных
ms.date: 06/14/2016
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database, pausing and resuming
- pausing Stretch Database
- resuming Stretch Database
ms.assetid: 65d6a990-b295-41b2-97f9-7b6bf3000e4d
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: 5146c258c099c487643ca343ecd06402fc623c84
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469009"
---
# <a name="pause-and-resume-data-migration-stretch-database"></a>Приостановка и возобновление переноса данных (Stretch Database)
[!INCLUDE [sqlserver2016-windows-only](../../includes/applies-to-version/sqlserver2016-windows-only.md)]


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
В SQL Server Management Studio откройте **монитор Stretch Database** и проверьте значение столбца **Состояние миграции**. Дополнительные сведения см. в статье [Мониторинг переноса данных и устранение неполадок](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).

### <a name="use-transact-sql-to-check-whether-migration-is-active-or-paused"></a>С помощью Transact-SQL проверьте, активна миграция или приостановлена.
Запросите представление каталога **sys.remote_data_archive_tables** и проверьте значение в столбце **is_migration_paused** . Дополнительные сведения см. в разделе [sys.remote_data_archive_tables](../../relational-databases/system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-tables.md).

## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Мониторинг переноса данных и устранение неполадок](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md) 
  
