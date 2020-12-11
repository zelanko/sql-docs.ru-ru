---
description: sys.dm_column_store_object_pool (Transact-SQL)
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
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e258c1b095c4b43ebf23957a721d40c5254d6edc
ms.sourcegitcommit: 2991ad5324601c8618739915aec9b184a8a49c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329948"
---
# <a name="sysdm_column_store_object_pool-transact-sql"></a>sys.dm_column_store_object_pool (Transact-SQL)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

 Возвращает количество различных типов использования пула памяти объектов для объектов индекса columnstore.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|INT|Идентификатор базы данных. Это значение уникально в пределах экземпляра базы данных SQL Server или сервера базы данных SQL Azure. |  
|**object_id**|INT|Идентификатор объекта. Объект является одним из object_types. | 
|**index_id**|INT|Идентификатор индекса columnstore.|  
|**partition_number**|BIGINT|Номер секции внутри индекса или кучи (нумерация начинается с 1). Каждая таблица или представление имеет по крайней мере одну секцию.| 
|**column_id**|INT|Идентификатор столбца columnstore. Это значение NULL для DELETE_BITMAP.| 
|**row_group_id**|INT|Идентификатор группы строк.|
|**object_type**|smallint|1 = COLUMN_SEGMENT<br /><br /> 2 = COLUMN_SEGMENT_PRIMARY_DICTIONARY<br /><br /> 3 = COLUMN_SEGMENT_SECONDARY_DICTIONARY<br /><br /> 4 = COLUMN_SEGMENT_BULKINSERT_DICTIONARY<br /><br /> 5 = COLUMN_SEGMENT_DELETE_BITMAP|  
|**object_type_desc**|nvarchar(60)|COLUMN_SEGMENT — сегмент столбца. `object_id` Идентификатор сегмента. В сегменте хранятся все значения одного столбца в пределах одного группы строк. Например, если таблица содержит 10 столбцов, то для каждого группы строк используется 10 сегментов столбцов. <br /><br /> COLUMN_SEGMENT_PRIMARY_DICTIONARY — глобальный словарь, содержащий сведения о поиске для всех сегментов столбцов в таблице.<br /><br /> COLUMN_SEGMENT_SECONDARY_DICTIONARY — локальный словарь, связанный с одним столбцом.<br /><br /> COLUMN_SEGMENT_BULKINSERT_DICTIONARY — другое представление глобального словаря. Это обеспечивает обратный поиск значения для dictionary_id. Используется для создания сжатых сегментов в рамках перемещения кортежей или при выполнении групповой загрузки.<br /><br /> COLUMN_SEGMENT_DELETE_BITMAP — битовая карта, которая отслеживает удаления сегментов. Для каждой секции имеется одно битовое изображение удаления.|  
|**access_count**|INT|Число обращений на чтение или запись к этому объекту.|  
|**memory_used_in_bytes**|BIGINT|Память, используемая этим объектом в пуле объектов.|  
|**object_load_time**|DATETIME|Время, когда object_id был помещен в пул объектов.|  
  
## <a name="permissions"></a>Разрешения  

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] необходимо `VIEW SERVER STATE` разрешение.   
В базах данных SQL Basic, S0 и S1, а также для баз данных в эластичных пулах `Server admin` `Azure Active Directory admin` требуется учетная запись или. Для всех остальных целей службы базы данных SQL `VIEW DATABASE STATE` разрешение требуется в базе данных.   
 
## <a name="see-also"></a>См. также:  
  
 [Динамические административные представления и функции, связанные с индексами &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys.dm_db_index_operational_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Наблюдение и настройка производительности](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
 [Индексы Columnstore. Обзор](../../relational-databases/indexes/columnstore-indexes-overview.md) 
  
