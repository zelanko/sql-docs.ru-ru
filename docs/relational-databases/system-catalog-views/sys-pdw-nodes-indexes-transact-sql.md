---
title: sys.pdw_nodes_indexes (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 261bcb7f-a906-4979-b274-bc5f1aa66426
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 04591e83fdfd8222a84480f983b21a6d77d51da2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="syspdwnodesindexes-transact-sql"></a>sys.pdw_nodes_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Возвращает индексы для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Идентификатор объекта, к которому принадлежит данный индекс.||  
|имя|**sysname**|Имя индекса. Имя является уникальным только в пределах объекта. NULL = куча.||  
|index_id|**int**|Идентификатор индекса. index_id уникально только в пределах объекта.<br /><br /> 0 = куча;<br /><br /> 1 = кластеризованный индекс;<br /><br /> > 1 = некластеризованный индекс||  
|Тип|**tinyint**|Тип индекса:<br /><br /> 0 = куча;<br /><br /> 1 = кластеризованный<br /><br /> 2 = некластеризованные<br /><br /> 5 = кластеризованный индекс columnstore с оптимизацией памяти xVelocity|  
|type_desc|**nvarchar(60)**|Описание типа индекса.<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> КЛАСТЕРИЗОВАННЫЙ ИНДЕКС COLUMNSTORE||  
|is_unique|**бит**|0 = индекс не уникален.|Значение всегда равно 0.|  
|data_space_id|**int**|Идентификатор пространства данных для этого индекса. Пространством данных может быть или файловая группа, или схема секционирования.<br /><br /> 0 = object_id является табличной функции.||  
|ignore_dup_key|**бит**|0 = параметр IGNORE_DUP_KEY имеет значение OFF.|Значение всегда равно 0.|  
|is_primary_key|**бит**|1 = индекс является частью ограничения PRIMARY KEY.|Значение всегда равно 0.|  
|is_unique_constraint|**бит**|1 = индекс является частью ограничения UNIQUE.|Значение всегда равно 0.|  
|fill_factor|**tinyint**|> 0 = процентный показатель FILLFACTOR, использованный при создании или повторном создании индекса.<br /><br /> 0 = значение по умолчанию.|Значение всегда равно 0.|  
|is_padded|**бит**|0 = параметр PADINDEX имеет значение OFF.|Значение всегда равно 0.|  
|is_disabled|**бит**|1 = индекс отключен.<br /><br /> 0 = индекс не отключен.||  
|is_hypothetical|**бит**|0 = индекс не является гипотетическим.|Значение всегда равно 0.|  
|allow_row_locks|**бит**|1 = индекс допускает блокировки строк.|Всегда имеет значение 1.|  
|allow_page_locks|**бит**|1 = индекс допускает блокировки страниц.|Всегда имеет значение 1.|  
|has_filter|**бит**|0 = индекс без фильтра.|Значение всегда равно 0.|  
|filter_definition|**nvarchar(max)**|Выражение для подмножества строк, включенного в фильтруемый индекс.|Значение всегда равно NULL.|  
|pdw_node_id|**int**|Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] узла.|NOT NULL|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
