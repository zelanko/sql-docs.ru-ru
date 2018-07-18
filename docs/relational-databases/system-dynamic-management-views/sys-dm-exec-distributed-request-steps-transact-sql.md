---
title: sys.dm_exec_distributed_request_steps (Transact-SQL) | Документация Майкрософт
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
- SYS.DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_distributed_request_steps
- sys.dm_exec_distributed_request_steps management view
ms.assetid: 1954541d-b716-4e03-8fcc-7022f428e01d
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f226ff8c5f18a0e812c6a457fe3382cb8f7b8d84
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37982596"
---
# <a name="sysdmexecdistributedrequeststeps-transact-sql"></a>sys.dm_exec_distributed_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех шагов, составляющих конкретный запрос PolyBase или запросов. Он содержит одну строку для каждого действия запроса.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**int**|значение execution_id и step_index составляющие ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|См. в разделе с кодом в [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|**int**|Позиция этого шага в последовательности действий, составляющих запрос.|0 (n-1) для запроса с n шагов.|  
|operation_type|**nvarchar(128)**|Тип операции, представленное в этом действии.|«MoveOperation», «OnOperation», «RandomIDOperation», «RemoteOperation», «ReturnOperation», «ShuffleMoveOperation», «TempTablePropertiesOperation», «DropDiagnosticsNotifyOperation», «HadoopShuffleOperation», «HadoopBroadCastOperation», «HadoopRoundRobinOperation»|  
|distribution_type|**nvarchar(32)**|Где выполняется шаг.|«Возможные «,» AllDistributions, «ComputeNode», «Distribution», «AllNodes», «SubsetNodes», «SubsetDistributions,» не задано».|  
|значение параметра location_type действия|**nvarchar(32)**|Где выполняется шаг.|«Вычисления», «Head» или «DMS». Все действия перемещения данных показывают «DMS».|  
|status|**nvarchar(32)**|Состояние этого шага|«Ожидание» «Выполняется», «Завершено», «Сбой», «UndoFailed», «PendingCancel», «отменено», «Отменено», «Прервано»|  
|error_id|**nvarchar(36)**|Уникальный идентификатор, связанный с этим шагом, если таковые имеются ошибки|См. в разделе идентификатор [sys.dm_exec_compute_node_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md), или значение NULL, если не возникло ошибок.|  
|start_time|**datetime**|Время начала выполнения шага|Меньше или равным текущее время и больше или равна end_compile_time запроса, к которой принадлежит этот шаг.|  
|end_time|**datetime**|Время, по которому этот шаг завершил выполнение, было отменено и сбой.|Меньше или равно текущего времени и размером менее start_time, очереди или значение NULL для шагов в настоящее время выполнения.|  
|total_elapsed_time|**int**|Общее количество времени этапа запроса на выполнение, в миллисекундах|Между 0 и разница между end_time и start_time. 0 для шаги в очереди.|  
|row_count|**bigint**|Общее число строк, измененных или возвращаемый этим запросом|для действия, которые не изменить или не возвращают данные, число строк, затронутых в противном случае — значение 0. Значение -1 для действия DMS.|  
|command|nvarchar(4000)|Содержит полный текст команды этого шага.|Любая строка допустимым запросом для шага. Усечено, если длиной более 4000 символов.|  
  
## <a name="see-also"></a>См. также  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
