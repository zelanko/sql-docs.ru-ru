---
title: sys.dm_exec_distributed_sql_requests (Transact-SQL) | Документация Майкрософт
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
- DM_EXEC_DISTRIBUTED_SQL_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_SQL_REQUESTS_TSQL
- DM_EXEC_DISTRIBUTED_SQL_REQUESTS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- sys.dm_exec_distributed_requests management view
- dm_exec_distributed_requests management view
ms.assetid: d065dc01-35d4-472f-9554-53ac41e7d104
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0fb08fe6acae5630ae2be35721b48155fc5509b8
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43091271"
---
# <a name="sysdmexecdistributedsqlrequests-transact-sql"></a>sys.dm_exec_distributed_sql_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех дистрибутивов SQL-запроса как часть действия SQL в запросе.  В этом представлении отображаются данные для последней 1000 запросов; активные запросы всегда имеют данные в этом представлении.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|значение execution_id и step_index составляющие ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|См. в разделе с кодом в [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)|  
|step_index|**int**|Индекс, это распределение является частью этапа запроса.|См. в разделе step_index в [sys.dm_exec_distributed_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md).|  
|compute_node_id|**int**|Тип операции, представленное в этом действии.|См. в разделе compute_node_id в [sys.dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|distribution_id|**int**|Где выполняется шаг.|Значение -1 для запросов, выполняемых на уровне узла не области распространения.|  
|status|**nvarchar(32)**|Состояние этого шага|Active, отмененные, завершенных, неудачных, в очереди|  
|error_id|**nvarchar(36)**|Уникальный идентификатор, связанный с этим шагом, если таковые имеются ошибки|См. в разделе идентификатор [sys.dm_exec_compute_node_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md), или значение NULL, если не возникло ошибок.|  
|start_time|**datetime**|Время начала выполнения шага|Меньше или равным текущее время и больше или равна end_compile_time запроса, к которой принадлежит этот шаг.|  
|end_time|**datetime**|Время, по которому этот шаг завершил выполнение, было отменено и сбой.|Меньше или равно текущего времени и размером менее start_time, очереди или значение NULL для шагов в настоящее время выполнения.|  
|total_elapsed_time|**int**|Общее количество времени этапа запроса на выполнение, в миллисекундах|Между 0 и разница между end_time и start_time. 0 для шаги в очереди.|  
|row_count|**bigint**|Общее число строк, измененных или возвращаемый этим запросом|для действия, которые не изменить или не возвращают данные, число строк, затронутых в противном случае — значение 0. Значение -1 для действия DMS.|  
|spid|**int**|Идентификатор сеанса в экземпляре SQL Server, выполнив распределение запросов||  
|command|nvarchar(4000)|Содержит полный текст команды этого шага.|Любая строка допустимым запросом для шага. Усечено, если длиной более 4000 символов.|  
  
## <a name="see-also"></a>См. также  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
