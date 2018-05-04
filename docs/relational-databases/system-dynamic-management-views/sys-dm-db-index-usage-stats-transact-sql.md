---
title: sys.dm_db_index_usage_stats (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_index_usage_stats_TSQL
- sys.dm_db_index_usage_stats
- sys.dm_db_index_usage_stats_TSQL
- dm_db_index_usage_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_index_usage_stats dynamic management view
ms.assetid: d06a001f-0f72-4679-bc2f-66fff7958b86
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 736f8b10f238f8f1629da432491f57796ad40b57
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmdbindexusagestats-transact-sql"></a>sys.dm_db_index_usage_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает количество различных операций с индексами и время, которое было затрачено на последнее выполнение операции каждого типа.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Чтобы избежать предоставления этих сведений, все строки, содержащие данные, не принадлежащие к подключенному клиенту, фильтруются.  
  
> [!NOTE]  
>  **sys.dm_db_index_usage_stats** не возвращает сведения об индексах оптимизированных для памяти. Сведения об использовании индекса, оптимизированного для памяти см. в разделе [sys.dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md).  
  
> [!NOTE]  
>  Для вызова данного представления от [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте **sys.dm_pdw_nodes_db_index_usage_stats**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**smallint**|Идентификатор базы данных, в которой определены таблица или представление.|  
|**object_id**|**int**|Идентификатор таблицы или представления, для которых определен индекс.|  
|**index_id**|**int**|Идентификатор индекса.|  
|**user_seeks**|**bigint**|Количество операций поиска по запросам пользователя.|  
|**user_scans**|**bigint**|Количество операций просмотра по запросам пользователя, не использующих «поиск» предиката.|  
|**user_lookups**|**bigint**|Количество уточняющих запросов для запросов пользователей.|  
|**user_updates**|**bigint**|Количество операций обновления по запросам пользователя. Сюда относится Insert, Delete и обновляет представляет количество действия, выполненные не фактические обработанных строк. Например при удалении 1000 строк в одной инструкции, это число с приращением 1|  
|**last_user_seek**|**datetime**|Время последней операции поиска, выполненной пользователем.|  
|**last_user_scan**|**datetime**|Время последней операции просмотра, выполненной пользователем.|  
|**last_user_lookup**|**datetime**|Время последней операции поиска соответствия, выполненной пользователем.|  
|**last_user_update**|**datetime**|Время последней операции обновления, выполненной пользователем.|  
|**system_seeks**|**bigint**|Количество операций поиска по системным запросам.|  
|**system_scans**|**bigint**|Количество операций просмотра по системным запросам.|  
|**system_lookups**|**bigint**|Количество уточняющих запросов для системных запросов.|  
|**system_updates**|**bigint**|Количество операций обновления по системным запросам.|  
|**last_system_seek**|**datetime**|Время последней системной операции поиска.|  
|**last_system_scan**|**datetime**|Время последней системной операции просмотра.|  
|**last_system_lookup**|**datetime**|Время последнего системного уточняющего запроса.|  
|**last_system_update**|**datetime**|Время последней системной операции обновления.|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="remarks"></a>Замечания  
 Каждая отдельная операция поиска, просмотра, уточняющего запроса или обновления на заданном индексе при выполнении одного запроса засчитывается как использование этого индекса и увеличивает на единицу соответствующий счетчик в данном представлении. Данные выводятся как для операций, вызванных пользовательскими запросами, так и для операций, вызванных внутренними запросами, например при выполнении операции просмотра для сбора статистики.  
  
 **User_updates** счетчика указывает уровень обслуживания индекса, вставки, обновления или операции delete в базовой таблице или представлении. С помощью этого представления можно определять, какие индексы используются приложениями лишь в незначительной степени. Можно также определять, какие индексы привносят дополнительную нагрузку, связанную с обслуживанием. Стоит рассмотреть возможность удаления индексов, вызывающих дополнительную нагрузку, связанную с их обслуживанием, но не использующихся для выполнения запросов или использующихся лишь иногда.  
  
 При запуске службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) счетчики сбрасываются в нуль. Кроме того, когда база данных отсоединяется или останавливается (например, если аргументу AUTO_CLOSE присвоено значение ON), из представления удаляются все строки, связанные с этой базой данных.  
  
 При использовании индекса строка будет добавлена в **sys.dm_db_index_usage_stats** Если строка еще не существует для индекса. При добавлении строки ее счетчики вначале сбрасываются в нуль.  
  
 При обновлении до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], в sys.dm_db_index_usage_stats удаляются записи. Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], сохраняются как до выпуска [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].  
  
## <a name="permissions"></a>Разрешения  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.  
  
## <a name="see-also"></a>См. также  

 [Динамические административные представления и функции, связанные с индексами &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys.dm_db_index_operational_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Наблюдение и настройка производительности](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  


