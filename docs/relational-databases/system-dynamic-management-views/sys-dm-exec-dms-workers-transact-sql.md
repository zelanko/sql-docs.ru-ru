---
title: sys.dm_exec_dms_workers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8a31b03208eba573fc6bd50f2348733ef0a07c2b
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52418365"
---
# <a name="sysdmexecdmsworkers-transact-sql"></a>sys.dm_exec_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех рабочих процессов, выполнив действия DMS.  
  
 В этом представлении отображаются данные для последней 1000 запросов и активных запросов; активные запросы всегда имеют данные в этом представлении.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|Запрос, что этим исполнителем DMS of.request_id часть, step_index, и dms_step_index формируют ключ для этого представления.||  
|step_index|**int**|Запрос шаг, который входит данный исполнитель DMS.|См. в разделе индекс этапа в [sys.dm_exec_distributed_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Шаг в плане DMS, на котором выполняется этот рабочий процесс.|См. в разделе [sys.dm_exec_dms_workers (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md)|  
|compute_node_id|**int**|Узел, который выполняется рабочая роль.|См. в разделе [sys.dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|distribution_id|**int**|||  
|Тип|**nvarcha(32)**|||  
|status|**nvarchar(32)**|Состояние этого шага|«Ожидание» «Выполняется», «Завершено», «Сбой», «UndoFailed», «PendingCancel», «отменено», «Отменено», «Прервано»|  
|bytes_per_sec|**bigint**|||  
|bytes_processed|**bigint**|||  
|rows_processed|**bigint**|||  
|start_time|**datetime**|Время начала выполнения шага|Меньше или равным текущее время и больше или равна end_compile_time запроса, к которой принадлежит этот шаг.|  
|end_time|**datetime**|Время, по которому этот шаг завершил выполнение, было отменено и сбой.|Меньше или равно текущего времени и размером менее start_time, очереди или значение NULL для шагов в настоящее время выполнения.|  
|total_elapsed_time|**int**|Общее количество времени этапа запроса на выполнение, в миллисекундах|Между 0 и разница между end_time и start_time. 0 для шаги в очереди.|  
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
 [PolyBase, устранение неполадок с помощью динамических административных представлений](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
