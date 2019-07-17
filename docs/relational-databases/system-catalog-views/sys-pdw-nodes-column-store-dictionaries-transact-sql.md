---
title: sys.pdw_nodes_column_store_dictionaries (Transact-SQL) | Документация Майкрософт
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.custom: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 7ae1c2e4-45c0-4880-a692-1f299fbcfd19
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7a588d23d5e3e7f9cb314342a739ceb8e051ca2c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059383"
---
# <a name="syspdwnodescolumnstoredictionaries-transact-sql"></a>sys.pdw_nodes_column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит по строке для каждого словаря, используемого в индексах columnstore. Словари используются для кодирования некоторых, но не всех типов данных, поэтому не все столбцы в индексе columnstore имеют словари. Словарь может существовать в качестве основного словаря (для всех сегментов) и, возможно, для других вспомогательных словарей, используемых для подмножества сегментов столбца.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Указывает идентификатор секции. Уникален в базе данных.|  
|**hobt_id**|**bigint**|Идентификатор кучи или индекс сбалансированного дерева (hobt) для таблицы, в которой содержится индекс columnstore.|  
|**column_id**|**int**|Идентификатор столбца columnstore.|  
|**dictionary_id**|**int**|Идентификатор словаря.|  
|**version**|**int**|Версия формата словаря.|  
|**type**|**int**|Тип словаря:<br /><br /> 1 - hash, словарь, содержащий **int** значения<br /><br /> 2 - не используется<br /><br /> 3 — хэш-словарь, содержащий строковые значения<br /><br /> 4 - словарь, содержащий hash **float** значения|  
|**last_id**|**int**|Последний идентификатор данных в словаре.|  
|**entry_count**|**bigint**|Количество записей в словаре.|  
|**on_disc_size**|**bigint**|Размер словаря в байтах.|  
|**pdw_node_id**|**int**|Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] узла.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW SERVER STATE.  
  
## <a name="see-also"></a>См. также  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
 [Создание ИНДЕКСА COLUMNSTORE &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)  
  
  
