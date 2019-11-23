---
title: sys. dm_exec_compute_node_errors (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_COMPUTE_NODE_ERRORS_TSQL
- DM_EXEC_COMPUTE_NODE_ERRORS
- DM_EXEC_COMPUTE_NODE_ERRORS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase
- PolyBase, views
- dm_exec_compute_node_errors
- sys.dm_exec_compute_node_errors management view
ms.assetid: 9a03c039-70e4-4974-95d8-d3fa45984ffb
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b074da717a2c5deac9d576da938d1229dafeac77
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532792"
---
# <a name="sysdm_exec_compute_node_errors-transact-sql"></a>sys. dm_exec_compute_node_errors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Возвращает ошибки, возникающие на вычисленных узлах Polybase.  
  
|Column Name|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|error_id|`nvarchar(36)`|Уникальный числовой идентификатор, связанный с ошибкой.|Уникальные для всех ошибок запросов в системе|  
|источник|`nvarchar(255)`|Описание исходного потока или процесса||  
|Тип|`nvarchar(255)`|Тип ошибки.||  
|create_time|`datetime`|Время возникновения ошибки||  
|compute_node_id|`int`|Идентификатор конкретного расчетного узла|См. compute_node_id из процедуры [sys &#40;. DM_EXEC_COMPUTE_NODES Transact&#41; -SQL](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)|  
|rexecution_id|`nvarchar(36)`|Идентификатор запроса Polybase, если он имеется.||  
|spid|`int`|Идентификатор сеанса SQL Server||  
|thread_id|`int`|Числовой идентификатор потока, в котором произошла ошибка.||  
|подробности|nvarchar(4000)|Полное описание ошибки.||
|compute_pool_id|`int`|Уникальный идентификатор пула.|

  
## <a name="see-also"></a>См. также статью  
 [Устранение неполадок в polybase с помощью динамических административных представлений](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления &#40;, связанные с базами данных TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
