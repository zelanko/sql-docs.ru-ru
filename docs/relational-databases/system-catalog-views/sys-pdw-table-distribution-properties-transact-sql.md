---
title: sys. pdw_table_distribution_properties (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 12/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 639a7475-7c92-41e0-a8ab-ad630eb5aea3
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b0e93eebd56579785a2673f4a38846350c737c3f
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86196822"
---
# <a name="syspdw_table_distribution_properties-transact-sql"></a>sys. pdw_table_distribution_properties (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит сведения о распределении таблиц.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|Идентификатор таблицы, для которой были указаны свойства три.||  
|**distribution_policy**|**tinyint**|0 = НЕ ОПРЕДЕЛЕНО<br /><br /> 1 = НЕТ<br /><br /> 2 = ХЭШ<br /><br /> 3 = РЕПЛИЦИРОВАТЬ<br /><br /> 4 = ROUND_ROBIN||  
|**distribution_policy_desc**|**nvarchar(60)**|НЕ ОПРЕДЕЛЕНО, НЕТ, ХЭШ, РЕПЛИКАЦИЯ, ROUND_ROBIN|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Возвращает либо HASH, ROUND_ROBIN, либо REPLICATE.|  
  
## <a name="see-also"></a>См. также  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md) (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
  
  
