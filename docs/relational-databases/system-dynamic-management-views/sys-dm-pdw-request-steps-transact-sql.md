---
title: "sys.dm_pdw_request_steps (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/01/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cc563e88-0d34-436e-b914-b60d6ee0d50b
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3c98aeb3ebc26d6ffd762e301c915b1522ce888a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwrequeststeps-transact-sql"></a>sys.dm_pdw_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех шагов создания данного запроса или запроса в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Он содержит одну строку для каждого действия запроса.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|идентификатор_запроса и step_index составляющие ключ для этого представления.<br /><br /> Уникальный числовой идентификатор, связанный с запросом.|В разделе request_id в [sys.dm_pdw_exec_requests &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|идентификатор_запроса и step_index составляющие ключ для этого представления.<br /><br /> Позиция этого шага в последовательности действий, составляющих запрос.|0 (n-1) для запроса с n шагов.|  
|operation_type|**nvarchar(35)**|Тип операции, представленное в этом действии.|**Операций плана запросов DMS:** «ReturnOperation», «PartitionMoveOperation», «MoveOperation», «BroadcastMoveOperation», «ShuffleMoveOperation», «TrimMoveOperation», «CopyOperation», «DistributeReplicatedTableMoveOperation»<br /><br /> **Операции план запроса SQL:** «OnOperation», «RemoteOperation»<br /><br /> **Другие операции плана запроса:** «MetaDataCreateOperation», «RandomIDOperation»<br /><br /> **Внешние операции для операций чтения:** «HadoopShuffleOperation», «HadoopRoundRobinOperation», «HadoopBroadcastOperation»<br /><br /> **Внешние операции для MapReduce:** «HadoopJobOperation», «HdfsDeleteOperation»<br /><br /> **Внешние операции для записи:** «ExternalExportDistributedOperation», «ExternalExportReplicatedOperation», «ExternalExportControlOperation»<br /><br /> Дополнительные сведения см. в разделе «Основные сведения о планов запросов» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].|  
|distribution_type|**nvarchar(32)**|Тип распределения, которые будут подвергнуты этот шаг.|'AllNodes', 'AllDistributions', 'AllComputeNodes', 'ComputeNode', 'Distribution', 'SubsetNodes', 'SubsetDistributions', 'Unspecified'|  
|значение параметра location_type действия|**nvarchar(32)**|Где запущен этот шаг.|'Compute', 'Control', 'DMS'|  
|status|**nvarchar(32)**|Состояние этого шага.|Ожидающие выполнения завершения, не удалось, UndoFailed, PendingCancel отменено, отменены, прервана|  
|error_id|**nvarchar(36)**|Уникальный идентификатор ошибки, связанные с этим шагом, если таковые имеются.|В разделе error_id из [sys.dm_pdw_errors &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). Имеет значение NULL, если не возникло ошибок.|  
|start_time|**datetime**|Время начала выполнения шага.|Меньше или равно значению текущего времени и размером менее end_compile_time запроса, к которому принадлежит этот шаг. Дополнительные сведения о запросах см. в разделе [sys.dm_pdw_exec_requests &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|end_time|**datetime**|Время, по которому этот шаг завершил выполнение, была отменена или не удалось.|Меньше или равно значению текущего времени и размером менее start_time. Значение NULL для шагов, которые в настоящее время выполнения или в очереди.|  
|total_elapsed_time|**int**|Общее количество времени, запущенного действия запроса, в миллисекундах.|Между 0 и разницу между end_time и start_time. 0 для шаги в очереди.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time продолжает оставаться максимальное значение. Это условие будет создавать предупреждение «превышено максимальное значение.»<br /><br /> Максимальное значение в миллисекундах соответствует 24.8 дней.|  
|row_count|**bigint**|Общее число строк, изменен или возвращаемого этим запросом.|0 для действия, которые не изменить или возвращать данные. В противном случае — количество обработанных строк.|  
|command|**nvarchar(4000)**|Содержит полный текст команды этого шага.|Любая строка допустимым запросом для шага. Имеет значение NULL, если операция имеет тип MetaDataCreateOperation. Если более 4000 символов усекаются.|  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении, обратитесь к разделу максимальные значения представление системы в «Минимальное и максимальное значения» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и динамические административные представления хранилища параллельных данных &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
