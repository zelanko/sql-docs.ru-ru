---
title: sys.pdw_nodes_column_store_segments (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/28/2018
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e2fdf8e9-1b74-4682-b2d4-c62aca053d7f
caps.latest.revision: 9
author: hirokib
ms.author: elbutter;barbkess
manager: jrj
ms.workload: Inactive
ms.openlocfilehash: 8e3daa47eea78bb90c736a42e7e541bea62e5ac4
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="syspdwnodescolumnstoresegments-transact-sql"></a>sys.pdw_nodes_column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Содержит по одной строке для каждого столбца в индексе columnstore.  

| Имя столбца                 | Тип данных  | Описание                                                  |
| --------------------------- | ---------- | ------------------------------------------------------------ |
| **partition_id**            | **bigint** | Указывает идентификатор секции. Уникален в базе данных.     |
| **hobt_id**                 | **bigint** | Идентификатор кучи или индекс сбалансированного дерева (hobt) для таблицы, в которой содержится индекс columnstore. |
| **column_id**               | **int**    | Идентификатор столбца columnstore.                                |
| **segment_id**              | **int**    | Идентификатор сегмента столбца. Для обеспечения обратной совместимости имя столбца по-прежнему вызываться segment_id, несмотря на то, что это идентификатор группы строк Можно однозначно определить сегмент с помощью < hobt_id, partition_id, column_id >, < segment_id >. |
| **version**                 | **int**    | Версия формата сегмента столбца.                        |
| **encoding_type**           | **int**    | Тип кодировки, используемой для этого сегмента:<br /><br /> 1 = VALUE_BASED - строка/недвоичные с словарь (аналогично 4 с некоторые варианты внутренний)<br /><br /> 2 = VALUE_HASH_BASED - не строки или двоичного столбца с общими значениями в словаре<br /><br /> 3 = STRING_HASH_BASED - строка и двоичный столбец с общими значениями в словаре<br /><br /> 4 = STORE_BY_VALUE_BASED - строка/недвоичные с словарь<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED - строка и двоичный файл с словарь<br /><br /> Все кодировки воспользоваться бит упаковки и длин кодирования, когда это возможно. |
| **row_count**               | **int**    | Число строк в группе строк.                             |
| **has_nulls**               | **int**    | Значение 1, если сегмент столбца содержит значения NULL.                     |
| **base_id**                 | **bigint** | Идентификатор базового значения, если используется тип кодирования 1.  Если тип кодирования 1 не используется, значение base_id устанавливается значение 1. |
| **Величина**               | **float**  | Значение величины, если используется тип кодирования 1.  Если тип кодирования 1 не используется, то величина равен 1. |
| **primary__dictionary_id**  | **int**    | Идентификатор основного словаря. Ненулевое значение указывает на локальный словарь для данного столбца в текущем сегменте (т. е. группу строк). Значение -1 указывает, что отсутствует локальный словарь для этого сегмента. |
| **secondary_dictionary_id** | **int**    | Идентификатор дополнительного словаря. Ненулевое значение указывает на локальный словарь для данного столбца в текущем сегменте (т. е. группу строк). Значение -1 указывает, что отсутствует локальный словарь для этого сегмента. |
| **min_data_id**             | **bigint** | Минимальный идентификатор данных в сегменте столбца.                       |
| **max_data_id**             | **bigint** | Максимальный идентификатор данных в сегменте столбца.                       |
| **null_value**              | **bigint** | Значение, используемое для представления значений NULL.                               |
| **on_disk_size**            | **bigint** | Размер сегмента в байтах.                                    |
| **pdw_node_id**             | **int**    | Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] узла. |

## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

Присоедините sys.pdw_nodes_column_store_segments с другими системными таблицами для определения количества сегментов columnstore каждой логической таблицы. 

```sql
SELECT  sm.name           as schema_nm
,       tb.name           as table_nm
,       nc.name           as col_nm
,       nc.column_id
,       COUNT(*)          as segment_count
FROM    sys.[schemas] sm
JOIN    sys.[tables] tb                   ON  sm.[schema_id]          = tb.[schema_id]
JOIN    sys.[pdw_table_mappings] mp       ON  tb.[object_id]          = mp.[object_id]
JOIN    sys.[pdw_nodes_tables] nt         ON  nt.[name]               = mp.[physical_name]
JOIN    sys.[pdw_nodes_partitions] np     ON  np.[object_id]          = nt.[object_id]
                                          AND np.[pdw_node_id]        = nt.[pdw_node_id]
                                          AND np.[distribution_id]    = nt.[distribution_id]
JOIN    sys.[pdw_nodes_columns] nc        ON  np.[object_id]          = nc.[object_id]
                                          AND np.[pdw_node_id]        = nc.[pdw_node_id]
                                          AND np.[distribution_id]    = nc.[distribution_id]
JOIN    sys.[pdw_nodes_column_store_segments] rg  ON  rg.[partition_id]         = np.[partition_id]
                                                      AND rg.[pdw_node_id]      = np.[pdw_node_id]
                                                      AND rg.[distribution_id]  = np.[distribution_id]
                                                      AND rg.[column_id]        = nc.[column_id]
GROUP BY    sm.name
,           tb.name
,           nc.name
,           nc.column_id  
ORDER BY    table_nm
,           nc.column_id
,           sm.name
```

## <a name="permissions"></a>Разрешения  
 Необходимо разрешение **VIEW SERVER STATE**.  

## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [Создание ИНДЕКСА COLUMNSTORE &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)   
 [sys.pdw_nodes_column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  

  

