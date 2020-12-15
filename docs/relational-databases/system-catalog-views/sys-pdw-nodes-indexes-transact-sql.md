---
description: sys.pdw_nodes_indexes (Transact-SQL)
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: 173e1435cc8b8ffdee169f5d5955c54955f978c4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97462815"
---
# <a name="syspdw_nodes_indexes-transact-sql"></a>sys.pdw_nodes_indexes (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Возвращает индексы для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] .  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Идентификатор объекта, которому принадлежит этот индекс.||  
|name|**sysname**|Имя индекса. Имя уникально только в пределах объекта. NULL = куча.||  
|index_id|**int**|Идентификатор индекса. Значение index_id уникально только в пределах объекта.<br /><br /> 0 = куча;<br /><br /> 1 = кластеризованный индекс;<br /><br /> > 1 = некластеризованный индекс||  
|тип|**tinyint**|Тип индекса:<br /><br /> 0 = куча;<br /><br /> 1 = кластеризованный<br /><br /> 2 = некластеризованный.<br /><br /> 5 = кластеризованный индекс columnstore, оптимизированный для памяти xVelocity|  
|type_desc|**nvarchar(60)**|Описание типа индекса.<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> КЛАСТЕРИЗОВАННЫЙ ИНДЕКС COLUMNSTORE||  
|is_unique|**bit**|0 = индекс не уникален.|Всегда равно 0.|  
|data_space_id|**int**|Идентификатор пространства данных для этого индекса. Пространством данных может быть или файловая группа, или схема секционирования.<br /><br /> 0 = функция с табличным значением object_id.||  
|ignore_dup_key|**bit**|0 = параметр IGNORE_DUP_KEY имеет значение OFF.|Всегда равно 0.|  
|is_primary_key|**bit**|1 = индекс является частью ограничения PRIMARY KEY.|Всегда равно 0.|  
|is_unique_constraint|**bit**|1 = индекс является частью ограничения UNIQUE.|Всегда равно 0.|  
|fill_factor|**tinyint**|> 0 = процент FILLFACTOR, используемый при создании или перестроении индекса.<br /><br /> 0 = значение по умолчанию.|Всегда равно 0.|  
|is_padded|**bit**|0 = параметр PADINDEX имеет значение OFF.|Всегда равно 0.|  
|is_disabled|**bit**|1 = индекс отключен.<br /><br /> 0 = индекс не отключен.||  
|is_hypothetical|**bit**|0 = индекс не является гипотетическим.|Всегда равно 0.|  
|allow_row_locks|**bit**|1 = индекс допускает блокировки строк.|Всегда равно 1.|  
|allow_page_locks|**bit**|1 = индекс допускает блокировки страниц.|Всегда равно 1.|  
|has_filter|**bit**|0 = индекс без фильтра.|Всегда равно 0.|  
|filter_definition|**nvarchar(max)**|Выражение для подмножества строк, включенного в фильтруемый индекс.|Всегда имеет значение NULL.|  
|pdw_node_id|**int**|Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] узла.|NOT NULL|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога Azure Synapse Analytics и Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
