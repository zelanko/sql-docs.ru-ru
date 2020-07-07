---
title: sys. dm_column_store_object_pool (Transact-SQL) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 720eebdbc1898d0b3ce34fb9a2205c41d4898dd2
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012908"
---
# <a name="sysdm_column_store_object_pool-transact-sql"></a>sys. dm_column_store_object_pool (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

 Возвращает количество различных типов использования пула памяти объектов для объектов индекса columnstore.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|`database_id`|`int`|Идентификатор базы данных. Это значение уникально в пределах экземпляра базы данных SQL Server или сервера базы данных SQL Azure. |  
|`object_id`|`int`|Идентификатор объекта. Объект является одним из object_types. | 
|`index_id`|`int`|Идентификатор индекса columnstore.|  
|`partition_number`|`bigint`|Номер секции внутри индекса или кучи (нумерация начинается с 1). Каждая таблица или представление имеет по крайней мере одну секцию.| 
|`column_id`|`int`|Идентификатор столбца columnstore. Это значение NULL для DELETE_BITMAP.| 
|`row_group_id`|`int`|Идентификатор группы строк.|
|`object_type`|`smallint`|1 = COLUMN_SEGMENT<br /><br /> 2 = COLUMN_SEGMENT_PRIMARY_DICTIONARY<br /><br /> 3 = COLUMN_SEGMENT_SECONDARY_DICTIONARY<br /><br /> 4 = COLUMN_SEGMENT_BULKINSERT_DICTIONARY<br /><br /> 5 = COLUMN_SEGMENT_DELETE_BITMAP|  
|`object_type_desc`|`nvarchar(60)`|COLUMN_SEGMENT — сегмент столбца. `object_id`Идентификатор сегмента. В сегменте хранятся все значения одного столбца в пределах одного группы строк. Например, если таблица содержит 10 столбцов, то для каждого группы строк используется 10 сегментов столбцов. <br /><br /> COLUMN_SEGMENT_PRIMARY_DICTIONARY — глобальный словарь, содержащий сведения о поиске для всех сегментов столбцов в таблице.<br /><br /> COLUMN_SEGMENT_SECONDARY_DICTIONARY — локальный словарь, связанный с одним столбцом.<br /><br /> COLUMN_SEGMENT_BULKINSERT_DICTIONARY — другое представление глобального словаря. Это обеспечивает обратный поиск значения для dictionary_id. Используется для создания сжатых сегментов в рамках перемещения кортежей или при выполнении групповой загрузки.<br /><br /> COLUMN_SEGMENT_DELETE_BITMAP — битовая карта, которая отслеживает удаления сегментов. Для каждой секции имеется одно битовое изображение удаления.|  
|`access_count`|`int`|Число обращений на чтение или запись к этому объекту.|  
|`memory_used_in_bytes`|`bigint`|Память, используемая этим объектом в пуле объектов.|  
|`object_load_time`|`datetime`|Время, когда object_id был помещен в пул объектов.|  
  
## <a name="permissions"></a>Разрешения  

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   
 
## <a name="see-also"></a>См. также  
  
 [Динамические административные представления и функции, связанные с индексами &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys. dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys. indexes &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys. Objects &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Наблюдение и настройка производительности](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  
