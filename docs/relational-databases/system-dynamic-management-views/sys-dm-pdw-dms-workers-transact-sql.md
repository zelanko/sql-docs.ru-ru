---
title: sys. dm_pdw_dms_workers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0a284d18-3c46-4ffa-bcc9-689e660ee8b4
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6e5f295637db0e138caf324e3126707b9e0ea774
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899511"
---
# <a name="sysdm_pdw_dms_workers-transact-sql"></a>sys. dm_pdw_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения обо всех рабочих ролях, завершающих шаги DMS.  
  
|Имя столбца|Тип данных|Description|Диапазонный индекс|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar (32)**|Запрос, частью которого является эта Рабочая роль DMS.<br /><br /> request_id, step_index и dms_step_index образуют ключ для этого представления.|См. раздел request_id в [sys. dm_pdw_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Шаг запроса, частью которого является Рабочая роль DMS.<br /><br /> request_id, step_index и dms_step_index образуют ключ для этого представления.|См. раздел step_index в [sys. dm_pdw_request_steps &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Шаг в плане DMS, в котором выполняется этот рабочий процесс.<br /><br /> request_id, step_index и dms_step_index образуют ключ для этого представления.||  
|pdw_node_id|**int**|Узел, на котором запущена Рабочая роль.|См. раздел node_id в [sys. dm_pdw_nodes &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**Int**|Распределение, на котором работает Рабочая роль, если таковая имеется.|См. раздел distribution_id в [sys. pdw_distributions &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md).|  
|type|**nvarchar (32)**|Тип рабочего потока DMS, представляемый этой записью.|"DIRECT_CONVERTER", "DIRECT_READER", "FILE_READER", "HASH_CONVERTER", "HASH_READER", "ROUNDROBIN_CONVERTER", "EXPORT_READER", "EXTERNAL_READER", "EXTERNAL_WRITER", "PARALLEL_COPY_READER", "REJECT_WRITER", "WRITER"|  
|status|**nvarchar (32)**|Состояние рабочей роли DMS.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|bytes_per_sec|**bigint**|Пропускная способность чтения или записи за последнюю секунду.|Больше или равно 0. Значение NULL, если запрос был отменен или завершился неудачей до выполнения рабочего процесса.|  
|bytes_processed|**bigint**|Общее число байтов, обработанных этим исполнителем.|Больше или равно 0. Значение NULL, если запрос был отменен или завершился неудачей до выполнения рабочего процесса.|  
|rows_processed|**bigint**|Число строк, считанных или записанных для этого рабочего процесса.|Больше или равно 0. Значение NULL, если запрос был отменен или завершился неудачей до выполнения рабочего процесса.|  
|start_time|**datetime**|Время начала выполнения этого рабочего процесса.|Больше или равно времени начала шага запроса, к которому относится этот рабочий процесс. См. раздел [sys. dm_pdw_request_steps &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Время, когда выполнение завершилось, завершилось сбоем или было отменено.|Значение NULL для текущих или рабочих процессов в очереди. В противном случае — значение больше start_time.|  
|total_elapsed_time|**int**|Общее время, затраченное на выполнение, в миллисекундах.|Больше или равно 0.<br /><br /> Общее время, прошедшее с момента запуска или перезапуска системы. Если total_elapsed_time превышает максимальное значение для целого числа (24,8 дней в миллисекундах), это приведет к сбою материализации из-за переполнения.<br /><br /> Максимальное значение в миллисекундах эквивалентно 24,8 дням.|  
|cpu_time|**bigint**|Время ЦП, потребляемое этим исполнителем в миллисекундах.|Больше или равно 0.|  
|query_time|**int**|Период времени, по истечении которого SQL начинает возвращать строки в поток, в миллисекундах.|Больше или равно 0.|  
|buffers_available|**int**|Количество неиспользуемых буферов.| Значение NULL, если запрос был отменен или завершился неудачей до выполнения рабочего процесса.|  
|sql_spid|**int**|Идентификатор сеанса на SQL Server экземпляре, выполняющем работу для этой рабочей роли DMS.||  
|dms_cpid|**int**|Идентификатор процесса реального выполняемого потока.||  
|error_id|**nvarchar (36)**|Уникальный идентификатор ошибки, произошедшей во время выполнения этого рабочего процесса (при его наличии).|См. раздел error_id в [sys. dm_pdw_request_steps &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|source_info|**nvarchar (4000)**|Для читателя — спецификация исходных таблиц и столбцов.||  
|destination_info|**nvarchar (4000)**|Для модуля записи — спецификация целевых таблиц.||  
  
 Сведения о максимальном объеме строк, хранящихся в этом представлении, см. в разделе метаданные статьи [ограничения емкости](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
