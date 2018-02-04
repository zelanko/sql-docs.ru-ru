---
title: "sys.dm_exec_dms_workers (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_DMS_WORKERS_TSQL
- DM_EXEC_DMS_WORKERS_TSQL
- DM_EXEC_DMS_WORKERS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_dms_workers management view
- sys.dm_exec_dms_workers management view
ms.assetid: f468da29-78c3-4f10-8a3c-17905bbf46f2
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ec7edcfc352e2addf3ba69d5915a11b25f483eba
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecdmsworkers-transact-sql"></a>sys.dm_exec_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех работников, выполнив действия DMS.  
  
 В этом представлении отображаются данные для последних 1000 запросов и активных запросов; активные запросы всегда иметь эти данные, имеющиеся в этом представлении.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|Запрос, что этот рабочий процесс DMS часть of.request_id, step_index, и dms_step_index формируют ключ для этого представления.||  
|step_index|**int**|Запрос шаг, который входит в состав этого исполнителя DMS.|Индекс в разделе [sys.dm_exec_distributed_request_steps &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Шаг в плане DMS, на котором выполняется этот рабочий процесс.|See [sys.dm_exec_dms_workers (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md)|  
|compute_node_id|**int**|Узел, на котором выполняется рабочий процесс, на.|В разделе [sys.dm_exec_compute_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|distribution_id|**int**|||  
|type|**nvarcha(32)**|||  
|status|**nvarchar(32)**|Состояние этого шага|«Ожидание» «Выполняется», «Завершено», «Сбой», «UndoFailed», «PendingCancel», «отменено», «Отменено», «Прервано»|  
|bytes_per_sec|**bigint**|||  
|bytes_processed|**bigint**|||  
|rows_processed|**bigint**|||  
|start_time|**datetime**|Время начала выполнения шага|Меньше или равно значению текущего времени и размером менее end_compile_time запроса, к которому принадлежит этот шаг.|  
|end_time|**datetime**|Время, по которому этот шаг завершил выполнение, была отменена или не удалось.|Меньше или равно значению текущего времени и размером менее start_time присваивается значение NULL для шагов, которые в настоящее время выполнения или в очереди.|  
|total_elapsed_time|**int**|Суммарное время действия запроса на выполнение, в миллисекундах|Между 0 и разницу между end_time и start_time. 0 для шаги в очереди.|  
|cpu_time|**bigint**|||  
|query_time|**int**|||  
|buffers_available|**int**|||  
|dms_cpid|**int**|||  
|sql_spid|**int**|||  
|error_id|**nvarchar(36)**|||  
|source_info|**nvarchar(4000)**|||  
|destination_info|**nvarchar(4000)**|||  
|command|**nvarchar(4000)**|||  
  
## <a name="see-also"></a>См. также  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления &#40; относящиеся к базе данных Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
