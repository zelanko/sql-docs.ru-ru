---
title: sys.pdw_distributions (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
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
ms.assetid: 572b5187-9753-4063-adf8-65dea87d11f8
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4e7d8e8ea3fa08c79bd7b0e26078ad229ce17c1b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="syspdwdistributions-transact-sql"></a>sys.pdw_distributions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о распределениях на устройстве. В нем перечислены одну строку для каждого устройства распространения.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|distribution_id|**int**|Уникальный числовой идентификатор, связанная с распределением.<br /><br /> Ключ для этого представления.|от 1 до количество вычислительных узлов в устройстве, умноженное на количество распространением на вычислительном узле.|  
|pdw_node_id|**int**|Идентификатор узла, в которой это распределение.|В разделе pdw_node_id в [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|имя|**nvarchar(32)**|Строковый идентификатор, связанная с распределением, используется в качестве суффикса для распределенных таблиц.|Строка состоит из «A-Z», «a-z», "0-9', «_»,"-".|  
|position|**int**|Позиция распространения в узле соответствующих на других дистрибутивах, которых на этом узле.|от 1 до количество распространением на каждом узле.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
