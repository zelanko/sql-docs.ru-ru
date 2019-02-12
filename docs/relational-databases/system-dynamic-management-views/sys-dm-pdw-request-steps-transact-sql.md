---
title: sys.dm_pdw_request_steps (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cc563e88-0d34-436e-b914-b60d6ee0d50b
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 63a39ab5ace1ec3666b3f5c70cc628268304ce92
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56039055"
---
# <a name="sysdmpdwrequeststeps-transact-sql"></a>sys.dm_pdw_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех шагов создания данного запроса или запроса в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Он содержит одну строку для каждого действия запроса.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Идентификатор request_id и step_index составляющие ключ для этого представления.<br /><br /> Уникальный числовой идентификатор, связанный с запросом.|См. в разделе request_id в [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Идентификатор request_id и step_index составляющие ключ для этого представления.<br /><br /> Позиция этого шага в последовательности действий, составляющих запрос.|0 (n-1) для запроса с n шагов.|  
|operation_type|**nvarchar(35)**|Тип операции, представленное в этом действии.|**Операции плана запроса DMS:** «ReturnOperation», «PartitionMoveOperation», «MoveOperation», «BroadcastMoveOperation», «ShuffleMoveOperation», «TrimMoveOperation», «CopyOperation», «DistributeReplicatedTableMoveOperation»<br /><br /> **Операции плана запроса SQL:** «OnOperation», «RemoteOperation»<br /><br /> **Другие операции плана запросов:** «MetaDataCreateOperation», «RandomIDOperation»<br /><br /> **Внешние операции для операций чтения:** «HadoopShuffleOperation», «HadoopRoundRobinOperation», «HadoopBroadcastOperation»<br /><br /> **Внешние операции для MapReduce:** «HadoopJobOperation», «HdfsDeleteOperation»<br /><br /> **Внешние операции для операций записи:** «ExternalExportDistributedOperation», «ExternalExportReplicatedOperation», «ExternalExportControlOperation»<br /><br /> Дополнительные сведения см. в разделе «Основные сведения о планах запросов» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].|  
|distribution_type|**nvarchar(32)**|Тип распределения, которые будут подвергнуты этот шаг.|«AllNodes», «AllDistributions», «Возможные», «ComputeNode», «Distribution», «SubsetNodes», «SubsetDistributions», «Unspecified»|  
|location_type|**nvarchar(32)**|Когда выполняется этап.|«Вычисления», «Управление», «DMS»|  
|status|**nvarchar(32)**|Состояние этого шага.|Ожидающие выполнения, полный, сбой, UndoFailed, PendingCancel отменено, отменено, прервана|  
|error_id|**nvarchar(36)**|Уникальный идентификатор ошибок, связанных с этим шагом, если таковые имеются.|См. в разделе error_id из [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). Имеет значение NULL, если не возникло ошибок.|  
|start_time|**datetime**|Время начала выполнения шага.|Меньше или равным текущее время и больше или равна end_compile_time запроса, к которой принадлежит этот шаг. Дополнительные сведения о запросах см. в разделе [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|end_time|**datetime**|Время, по которому этот шаг завершил выполнение, было отменено и сбой.|Меньше или равно времени истечения текущего и больше или равна start_time. Очереди или значение NULL для шагов в настоящее время выполнения.|  
|total_elapsed_time|**int**|Общее количество времени этап запроса будет выполняться, в миллисекундах.|Между 0 и разница между end_time и start_time. 0 для шаги в очереди.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будут продолжать максимальное значение. Это условие будет создавать предупреждение «превышено максимальное значение.»<br /><br /> Максимальное значение в миллисекундах соответствует 24,8 дня.|  
|row_count|**bigint**|Общее число строк, изменить или возвращаемый этим запросом.|0 для действия, которые не изменить или не возвращать данные. В противном случае — число затронутых строк.|  
|command|**nvarchar(4000)**|Содержит полный текст команды этого шага.|Любая строка допустимым запросом для шага. Имеет значение NULL, если операция имеет тип MetaDataCreateOperation. Усечено, если длиной более 4000 символов.|  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе «минимальное и максимальное значения» максимальные значения представление системы в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
