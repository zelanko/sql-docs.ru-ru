---
title: "sys.dm_exec_distributed_sql_requests (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_SQL_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_SQL_REQUESTS_TSQL
- DM_EXEC_DISTRIBUTED_SQL_REQUESTS
dev_langs: TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- sys.dm_exec_distributed_requests management view
- dm_exec_distributed_requests management view
ms.assetid: d065dc01-35d4-472f-9554-53ac41e7d104
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 922f2ce79dbabe3670b3488299a530b2a28e0cc2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecdistributedsqlrequests-transact-sql"></a>sys.dm_exec_distributed_sql_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит сведения о все распределения запросов SQL в ходе выполнения шага SQL в запросе.  В этом представлении отображаются данные для последних 1000 запросов. активные запросы всегда иметь эти данные, имеющиеся в этом представлении.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|execution_id и step_index составляющие ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|В разделе с кодом в [sys.dm_exec_requests &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)|  
|step_index|**int**|Индекс в очередь это распределение является частью запроса.|В разделе step_index в [sys.dm_exec_distributed_request_steps &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md).|  
|compute_node_id|**int**|Тип операции, представленное в этом действии.|В разделе compute_node_id в [sys.dm_exec_compute_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|distribution_id|**int**|Где выполнении шага.|Значение -1 для запросов, которые выполняются в области узла не области распространения.|  
|status|**nvarchar(32)**|Состояние этого шага|Active, отмененные, завершенных, неудачных, обновляемых посредством очередей|  
|error_id|**nvarchar(36)**|Уникальный идентификатор, связанный с этим шагом, если таковые имеются ошибки|В разделе идентификатор [sys.dm_exec_compute_node_errors &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md), Значение NULL, если не возникло ошибок.|  
|start_time|**datetime**|Время начала выполнения шага|Меньше или равно значению текущего времени и размером менее end_compile_time запроса, к которому принадлежит этот шаг.|  
|end_time|**datetime**|Время, по которому этот шаг завершил выполнение, была отменена или не удалось.|Меньше или равно значению текущего времени и размером менее start_time присваивается значение NULL для шагов, которые в настоящее время выполнения или в очереди.|  
|total_elapsed_time|**int**|Суммарное время действия запроса на выполнение, в миллисекундах|Между 0 и разницу между end_time и start_time. 0 для шаги в очереди.|  
|row_count|**bigint**|Общее число строк, измененных или возвращаемого этим запросом|0 для действия, которые не изменить или возвращают данные, число строк, затронутых в противном случае. Значение -1 для действия DMS.|  
|spid|**int**|Идентификатор сеанса в экземпляре SQL Server, выполнив распределение запросов||  
|command|nvarchar(4000)|Содержит полный текст команды этого шага.|Любая строка допустимым запросом для шага. Если более 4000 символов усекаются.|  
  
## <a name="see-also"></a>См. также:  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления &#40; относящиеся к базе данных Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
