---
description: sys. pdw_table_distribution_properties (Transact-SQL)
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
ms.openlocfilehash: 580ce1c29f8c788e23cac3d2c78edf164118cb6d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475335"
---
# <a name="syspdw_table_distribution_properties-transact-sql"></a>sys. pdw_table_distribution_properties (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит сведения о распределении таблиц.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|Идентификатор таблицы, для которой были указаны свойства три.||  
|**distribution_policy**|**tinyint**|0 = НЕ ОПРЕДЕЛЕНО<br /><br /> 1 = НЕТ<br /><br /> 2 = ХЭШ<br /><br /> 3 = РЕПЛИЦИРОВАТЬ<br /><br /> 4 = ROUND_ROBIN||  
|**distribution_policy_desc**|**nvarchar(60)**|НЕ ОПРЕДЕЛЕНО, НЕТ, ХЭШ, РЕПЛИКАЦИЯ, ROUND_ROBIN|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Возвращает либо HASH, ROUND_ROBIN, либо REPLICATE.|  
  
## <a name="see-also"></a>См. также  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md) (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
  
  
