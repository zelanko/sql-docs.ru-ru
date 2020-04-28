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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "73532792"
---
# <a name="sysdm_exec_compute_node_errors-transact-sql"></a>sys. dm_exec_compute_node_errors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Возвращает ошибки, возникающие на вычисленных узлах Polybase.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|error_id|`nvarchar(36)`|Уникальный числовой идентификатор, связанный с ошибкой.|Уникальные для всех ошибок запросов в системе|  
|source|`nvarchar(255)`|Описание исходного потока или процесса||  
|type|`nvarchar(255)`|Тип ошибки.||  
|create_time|`datetime`|Время возникновения ошибки||  
|compute_node_id|`int`|Идентификатор конкретного расчетного узла|См. раздел compute_node_id из [sys. dm_exec_compute_nodes &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md) .|  
|rexecution_id|`nvarchar(36)`|Идентификатор запроса Polybase, если он имеется.||  
|spid|`int`|Идентификатор сеанса SQL Server||  
|thread_id|`int`|Числовой идентификатор потока, в котором произошла ошибка.||  
|подробности|nvarchar(4000)|Полное описание ошибки.||
|compute_pool_id|`int`|Уникальный идентификатор пула.|

  
## <a name="see-also"></a>См. также:  
 [Устранение неполадок в Polybase с помощью динамических административных представлений](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с базами данных &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
