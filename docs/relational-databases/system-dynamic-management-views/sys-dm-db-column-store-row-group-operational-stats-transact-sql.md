---
title: sys.dm_db_column_store_row_group_operational_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31b71c68-50a0-4fd8-a7fe-2d2292be1163
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 6872055c103d83dbf72d3cda3105d0197bb5a93b
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39544544"
---
# <a name="sysdmdbcolumnstorerowgroupoperationalstats-transact-sql"></a>sys.dm_db_column_store_row_group_operational_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает текущий ввода-вывода, блокировка, на уровне строк и метода доступа для сжатых групп строк в индексе columnstore. Используйте **sys.dm_db_column_store_row_group_operational_stats** для отслеживания времени выполнения пользовательских запросов должен ожидание выполнения чтения или записи в сжатую группу строк или секции индекса columnstore, а также задавать группах строк, которые возникают много операций ввода-вывода или пробки.  
  
 Индексы columnstore в памяти в данном DMV не отображаются.  
 
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор таблицы с индексом columnstore.|  
|**index_id**|**int**|Идентификатор индекса columnstore.|  
|**partition_number**|**int**|Номер секции внутри индекса или кучи (нумерация начинается с 1).|  
|**row_group_id**|**int**|Идентификатор группы строк в индексе columnstore. Он уникален внутри секции.|  
|**scan_count**|**int**|Число просмотров через группы строк с момента последнего перезапуска SQL.|  
|**delete_buffer_scan_count**|**int**|Сколько раз буфера удаления, использованный для определения удаленных строк в эту группу строк. Это включает в себя доступ к хэш-таблицы в памяти и базовой сбалансированного дерева.|  
|**index_scan_count**|**int**|Сколько раз было просмотрено секция индекса columnstore. Это то же самое для всех групп строк в секции.|  
|**rowgroup_lock_count**|**bigint**|Совокупное количество запросов блокировок для этой группы строк с момента последнего перезапуска SQL.|  
|**rowgroup_lock_wait_count**|**bigint**|Совокупное количество раз СУБД ожидал блокировку этой группы строк с момента последнего перезапуска SQL.|  
|**rowgroup_lock_wait_in_ms**|**bigint**|Совокупное количество миллисекунд ожидания ядра СУБД в эта блокировка группы строк с момента последнего перезапуска SQL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимы следующие разрешения:  
  
-   Разрешение CONTROL на таблицу, заданную свойством object_id.  
  
-   Разрешение VIEW DATABASE STATE для возврата сведений обо всех объектах в базе данных, с помощью шаблона @*object_id* = NULL  
  
 Предоставление разрешения VIEW DATABASE STATE позволяет всем объектам в базе данных быть возвращаемыми, независимо от любых разрешений CONTROL, запрещенных для определенных объектов.  
  
 Запрет разрешения VIEW DATABASE STATE запрещает всем объектам в базе данных быть возвращаемыми, независимо от любых разрешений CONTROL, предоставленных на определенные объекты. Кроме того, если шаблон базы данных @*database_id*= указано значение NULL, эта база данных пропускается.  
  
 Дополнительные сведения см. в разделе [динамические административные представления и функции &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с индексами &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Наблюдение и настройка производительности](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [sys.dm_db_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys.dm_db_index_usage_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md)   
 [sys.dm_os_latch_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md)   
 [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)   
 [sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
  

