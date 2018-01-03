---
title: "sys.pdw_nodes_column_store_segments (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: e2fdf8e9-1b74-4682-b2d4-c62aca053d7f
caps.latest.revision: "9"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b10564c7736dce2ab21cc83bed819606230e7b9
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="syspdwnodescolumnstoresegments-transact-sql"></a>sys.pdw_nodes_column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждого столбца в индексе columnstore.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Указывает идентификатор секции. Уникален в базе данных.|  
|**hobt_id**|**bigint**|Идентификатор кучи или индекс сбалансированного дерева (hobt) для таблицы, в которой содержится индекс columnstore.|  
|**Идентификатор column_id**|**int**|Идентификатор столбца columnstore.|  
|**segment_id**|**int**|Идентификатор сегмента столбца.|  
|**version**|**int**|Версия формата сегмента столбца.|  
|**encoding_type**|**int**|Тип кодировки, используемой для этого сегмента.|  
|**row_count**|**int**|Число строк в группе строк.|  
|**has_nulls**|**int**|Значение 1, если сегмент столбца содержит значения NULL.|  
|**base_id**|**bigint**|Идентификатор базового значения, если используется тип кодирования 1.  Если тип кодирования 1 не используется, значение base_id устанавливается значение 1.|  
|**Величина**|**float**|Значение величины, если используется тип кодирования 1.  Если тип кодирования 1 не используется, то величина равен 1.|  
|**primary__dictionary_id**|**int**|Идентификатор основного словаря.|  
|**secondary_dictionary_id**|**int**|Идентификатор дополнительного словаря. Возвращает значение -1, если дополнительный словарь отсутствует.|  
|**min_data_id**|**bigint**|Минимальный идентификатор данных в сегменте столбца.|  
|**max_data_id**|**bigint**|Максимальный идентификатор данных в сегменте столбца.|  
|**null_value**|**bigint**|Значение, используемое для представления значений NULL.|  
|**on_disk_size**|**bigint**|Размер сегмента в байтах.|  
|**pdw_node_id**|**int**|Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Примечание.|  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий запрос возвращает сведения о сегментах индекса columnstore.  
  
```sql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
```  
  
 Присоедините sys.pdw_nodes_column_store_segments с другими системными таблицами для определения количества строк и размера сегментов на диске.  
  
```  
SELECT o.name, css.hobt_id, css. column_id, css.pdw_node_id, css.row_count, css.on_disk_size  
FROM sys.pdw_nodes_column_store_segments AS css  
JOIN sys.pdw_nodes_partitions AS pnp  
    ON css.partition_id = pnp.partition_id  
JOIN sys.pdw_nodes_tables AS part  
    ON pnp.object_id = part.object_id   
    AND pnp.pdw_node_id = part.pdw_node_id  
JOIN sys.pdw_table_mappings AS TMap  
    ON part.name = TMap.physical_name  
JOIN sys.objects AS o  
    ON TMap.object_id = o.object_id  
ORDER BY css.hobt_id, css.column_id;  
```  
  
## <a name="permissions"></a>Разрешения  
 Требуется **VIEW SERVER STATE** разрешение.  
  
## <a name="see-also"></a>См. также:  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [СОЗДАТЬ индекс COLUMNSTORE &#40; Transact-SQL &#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)   
 [sys.pdw_nodes_column_store_dictionaries &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  
  
  

