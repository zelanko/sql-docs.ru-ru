---
title: sys. pdw_distributions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 572b5187-9753-4063-adf8-65dea87d11f8
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 12a3318f88a719ab70043e2685a475e14cf24fdc
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197403"
---
# <a name="syspdw_distributions-transact-sql"></a>sys. pdw_distributions (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит сведения о распределениях на устройстве. В нем отображается одна строка для каждого распределения устройства.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|distribution_id|**int**|Уникальный числовой идентификатор, связанный с распределением.<br /><br /> Ключ для этого представления.|1 на число единиц вычислений на устройстве, умноженное на число распределений на каждый узел вычислений.|  
|pdw_node_id|**int**|Идентификатор узла, на котором находится это распространение.|См. раздел pdw_node_id в [sys. dm_pdw_nodes &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|name|**nvarchar(32)**|Идентификатор строки, связанный с распределением, используемый в качестве суффикса в распределенных таблицах.|Строка, состоящая из "A-Z", "a-z", "0-9", "_", "-".|  
|position|**int**|Расположение распределения в узле, соответствующем другим распределениям на этом узле.|1 — число распределений на узел.|  
  
## <a name="see-also"></a>См. также  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md) (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
  
  
