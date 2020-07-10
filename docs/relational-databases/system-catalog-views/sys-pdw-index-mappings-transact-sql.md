---
title: sys. pdw_index_mappings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 3e51acd0ef179d4bb9bf85bed34593f9676db063
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86196792"
---
# <a name="syspdw_index_mappings-transact-sql"></a>sys. pdw_index_mappings (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Сопоставляет логические индексы с физическим именем, используемым на вычисленных узлах, как отражается уникальным сочетанием **object_id** таблицы, содержащей индекс, и **index_id** определенного индекса в этой таблице.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Идентификатор объекта для логической таблицы, в которой существует этот индекс. См. статью [sys. objects &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **physical_name** и **object_id** формируют ключ для этого представления.||  
|index_id|**nvarchar(32)**|Идентификатор индекса. См. статью [sys. indexes &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).||  
|physical_name|**nvarchar (36)**|Имя индекса в базах данных на вычисленных узлах.<br /><br /> **physical_name** и **object_id** формируют ключ для этого представления.||  
  
## <a name="see-also"></a>См. также  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
 [sys. pdw_table_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [sys. pdw_database_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
  
