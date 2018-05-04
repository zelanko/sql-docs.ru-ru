---
title: sys.dm_db_column_store_row_group_operational_stats (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31b71c68-50a0-4fd8-a7fe-2d2292be1163
caps.latest.revision: 6
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d051f1bfa08f49d5ad0549051afa823ac72e977c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmdbcolumnstorerowgroupoperationalstats-transact-sql"></a>sys.dm_db_column_store_row_group_operational_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает текущий ввод-вывод, блокировку, на уровне строк и метода доступа для сжатых группах строк в индексе columnstore. Используйте **sys.dm_db_column_store_row_group_operational_stats** для отслеживания время запроса пользователя необходимо ожидание выполнения чтения или записи в сжатую группу строк или секции индекса columnstore, а затем определить группах строк, которые появляются много операций ввода-вывода или присутствуют перегруженные участки.  
  
 Индексы columnstore в памяти в данном DMV не отображаются.  
 
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор таблицы с индексом columnstore.|  
|**index_id**|**int**|Идентификатор индекса columnstore.|  
|**partition_number**|**int**|Номер секции внутри индекса или кучи (нумерация начинается с 1).|  
|**row_group_id**|**int**|Идентификатор группы строк в индексе columnstore. Он уникален внутри секции.|  
|**scan_count**|**int**|Количество операций просмотра по группе строк с момента последнего перезапуска SQL.|  
|**delete_buffer_scan_count**|**int**|Число раз использования для определения строк, удаленных в этой группе строк буфера удаления. Это включает доступ к хэш-таблицы в памяти и базовой сбалансированного дерева.|  
|**index_scan_count**|**int**|Количество раз, когда проверенной секция индекса columnstore. Это значение одинаково для всех групп строк в секции.|  
|**rowgroup_lock_count**|**bigint**|Совокупное количество запросов блокировок для этой группы строк с момента последнего перезапуска SQL.|  
|**rowgroup_lock_wait_count**|**bigint**|Совокупное количество раз СУБД ожидал блокировку этой группы строк с момента последнего перезапуска SQL.|  
|**rowgroup_lock_wait_in_ms**|**bigint**|Совокупное количество миллисекунд ожидания компонент database engine на эта блокировка строк с момента последнего перезапуска SQL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимы следующие разрешения:  
  
-   Разрешение CONTROL на таблицу, заданную свойством object_id.  
  
-   Разрешение VIEW DATABASE STATE для возврата сведений обо всех объектах в базе данных, с помощью объекта подстановочный знак @*object_id* = NULL  
  
 Предоставление разрешения VIEW DATABASE STATE позволяет всем объектам в базе данных быть возвращаемыми, независимо от любых разрешений CONTROL, запрещенных для определенных объектов.  
  
 Запрет разрешения VIEW DATABASE STATE запрещает всем объектам в базе данных быть возвращаемыми, независимо от любых разрешений CONTROL, предоставленных на определенные объекты. Кроме того, если шаблон базы данных @*database_id*= указано значение NULL, эта база данных пропускается.  
  
 Дополнительные сведения см. в разделе [динамические административные представления и функции &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с индексами &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Monitor and Tune for Performance](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [sys.dm_db_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys.dm_db_index_usage_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md)   
 [sys.dm_os_latch_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md)   
 [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)   
 [sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
  

