---
title: sys.dm_exec_compute_nodes (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODES_TSQL
- DM_EXEC_COMPUTE_NODES
- SYS.DM_EXEC_COMPUTE_NODES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_compute_nodes management view
- PolyBase, views
- PolyBase management views
- dm_exec_compute_nodes management view
ms.assetid: 0de4b7a4-401f-4e2d-9ab0-c54587e05154
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2e0c2b19e9d790e25f78b88160b96a5f0d4d9eb8
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34464980"
---
# <a name="sysdmexeccomputenodes-transact-sql"></a>sys.dm_exec_compute_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит сведения об использовании управления данными PolyBase узлах. Он содержит одну строку для каждого узла.  
  
 Используйте это динамическое административное Представление, чтобы просмотреть список всех узлов в кластере горизонтального масштабирования с их роли, именем и IP-адрес.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом. Ключ для этого представления.|Уникален в пределах кластера масштабируемых независимо от типа.|  
|Тип|**nvarchar(32)**|Тип узла.|«ВЫЧИСЛЕНИЯ», «HEAD»|  
|имя|**nvarchar(32)**|Логическое имя узла.|Любая строка соответствующей длины.|  
|address|**nvarchar(32)**|P адрес этого узла.|Диапазон IP-адресов|  
  
## <a name="see-also"></a>См. также  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
