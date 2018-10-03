---
title: sys.dm_column_store_object_pool (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a8a58ca7-0a7d-4786-bfd9-e8894bd345dd
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f70f0a6f6c4dc8ba4e72b30918c882c103c9410f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47669112"
---
# <a name="sysdmcolumnstoreobjectpool-transact-sql"></a>sys.dm_column_store_object_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Возвращает количество различных типов объектов использование пула памяти для объектов индекса columnstore.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|`database_id`|`int`|Идентификатор базы данных. Является уникальным внутри экземпляра базы данных SQL Server или сервер базы данных Azure SQL. |  
|`object_id`|`int`|Идентификатор объекта. Объект является одним из object_types. | 
|`index_id`|`int`|Идентификатор индекса columnstore.|  
|`partition_number`|`bigint`|Номер секции внутри индекса или кучи (нумерация начинается с 1). Каждая таблица или представление имеет по крайней мере одну секцию.| 
|`column_id`|`int`|Идентификатор столбца columnstore. Имеет значение NULL для DELETE_BITMAP.| 
|`row_group_id`|`int`|Идентификатор группы строк.|
|`object_type`|`smallint`|1 = COLUMN_SEGMENT<br /><br /> 2 = COLUMN_SEGMENT_PRIMARY_DICTIONARY<br /><br /> 3 = COLUMN_SEGMENT_SECONDARY_DICTIONARY<br /><br /> 4 = COLUMN_SEGMENT_BULKINSERT_DICTIONARY<br /><br /> 5 = COLUMN_SEGMENT_DELETE_BITMAP|  
|`object_type_desc`|`nvarchar(60)`|COLUMN_SEGMENT — сегмент столбца. `object_id` Идентификатор сегмента. Сегмент сохраняет все значения для одного столбца в одну группу строк. Например если таблица содержит 10 столбцов, существуют 10 сегментов столбцов в каждой группе строк. <br /><br /> COLUMN_SEGMENT_PRIMARY_DICTIONARY — глобальный словарь, содержащий таблицы подстановок для всех сегментов столбцов в таблице.<br /><br /> COLUMN_SEGMENT_SECONDARY_DICTIONARY - локальный словарь, связанный с одним столбцом.<br /><br /> COLUMN_SEGMENT_BULKINSERT_DICTIONARY — другое представление глобальный словарь. Это обеспечивает обратный поиск значения к dictionary_id. Используется для создания сжатые сегменты в процессе переноса кортежей или массовой загрузки.<br /><br /> COLUMN_SEGMENT_DELETE_BITMAP — удаляет точечный рисунок, который отслеживает сегмента. Нет одного точечного рисунка delete на секцию.|  
|`access_count`|`int`|Количество чтения или записи обращается к этому объекту.|  
|`memory_used_in_bytes`|`bigint`|Объем памяти, используемый этим объектом в пул объекта.|  
|`object_load_time`|`datetime`|Часы и время при object_id была внесена в пул объекта.|  
  
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
  
  
