---
title: sys.pdw_nodes_indexes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 261bcb7f-a906-4979-b274-bc5f1aa66426
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c13e41abea44bdbe0f954518f42aab118360a155
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56012385"
---
# <a name="syspdwnodesindexes-transact-sql"></a>sys.pdw_nodes_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Возвращает индексы для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Идентификатор объекта, к которому принадлежит данный индекс.||  
|name|**sysname**|Имя индекса. Имя является уникальным только в пределах объекта. NULL = куча.||  
|index_id|**int**|Идентификатор индекса. index_id уникально только в пределах объекта.<br /><br /> 0 = куча;<br /><br /> 1 = кластеризованный индекс;<br /><br /> > 1 = индекс, отличные от кластерных||  
|Тип|**tinyint**|Тип индекса:<br /><br /> 0 = куча;<br /><br /> 1 = кластеризованный<br /><br /> 2 = некластеризованные<br /><br /> 5 = кластеризованный индекс columnstore с оптимизацией для памяти xVelocity|  
|type_desc|**nvarchar(60)**|Описание типа индекса.<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> КЛАСТЕРИЗОВАННЫЙ ИНДЕКС COLUMNSTORE||  
|is_unique|**bit**|0 = индекс не уникален.|Всегда равно 0.|  
|data_space_id|**int**|Идентификатор пространства данных для этого индекса. Пространством данных может быть или файловая группа, или схема секционирования.<br /><br /> 0 = object_id — это функция, возвращающих табличные значения.||  
|ignore_dup_key|**bit**|0 = параметр IGNORE_DUP_KEY имеет значение OFF.|Всегда равно 0.|  
|is_primary_key|**bit**|1 = индекс является частью ограничения PRIMARY KEY.|Всегда равно 0.|  
|is_unique_constraint|**bit**|1 = индекс является частью ограничения UNIQUE.|Всегда равно 0.|  
|fill_factor|**tinyint**|> 0 = процентный показатель FILLFACTOR, использованный при создании или повторном создании индекса.<br /><br /> 0 = значение по умолчанию.|Всегда равно 0.|  
|is_padded|**bit**|0 = параметр PADINDEX имеет значение OFF.|Всегда равно 0.|  
|is_disabled|**bit**|1 = индекс отключен.<br /><br /> 0 = индекс не отключен.||  
|is_hypothetical|**bit**|0 = индекс не является гипотетическим.|Всегда равно 0.|  
|allow_row_locks|**bit**|1 = индекс допускает блокировки строк.|Всегда имеет значение 1.|  
|allow_page_locks|**bit**|1 = индекс допускает блокировки страниц.|Всегда имеет значение 1.|  
|has_filter|**bit**|0 = индекс без фильтра.|Всегда равно 0.|  
|filter_definition|**nvarchar(max)**|Выражение для подмножества строк, включенного в фильтруемый индекс.|Значение всегда равно NULL.|  
|pdw_node_id|**int**|Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] узла.|NOT NULL|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
