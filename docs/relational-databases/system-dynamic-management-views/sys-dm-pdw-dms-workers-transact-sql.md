---
title: sys.dm_pdw_dms_workers (Transact-SQL) | Документация Майкрософт
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
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 96fd36d1710a166285fecba092735c7d2495271e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62690448"
---
# <a name="sysdmpdwdmsworkers-transact-sql"></a>sys.dm_pdw_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех рабочих процессов, выполнив действия DMS.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Запрос, который входит данный исполнитель DMS.<br /><br /> Идентификатор request_id step_index и dms_step_index формируют ключ для этого представления.|См. в разделе request_id в [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Запрос шаг, который входит данный исполнитель DMS.<br /><br /> Идентификатор request_id step_index и dms_step_index формируют ключ для этого представления.|См. в разделе step_index в [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Шаг в плане DMS, на котором выполняется этот рабочий процесс.<br /><br /> Идентификатор request_id step_index и dms_step_index формируют ключ для этого представления.||  
|pdw_node_id|**int**|Узел, который выполняется рабочая роль.|См. в разделе node_id в [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**Int**|Распределение, которое выполняется рабочая роль, если таковые имеются.|См. в разделе идентификатор distribution_id в [sys.pdw_distributions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md).|  
|type|**nvarchar(32)**|Тип DMS рабочий поток, который представляет эту запись.|«DIRECT_CONVERTER», «DIRECT_READER», «FILE_READER», «HASH_CONVERTER», «HASH_READER», «ROUNDROBIN_CONVERTER», «EXPORT_READER», «EXTERNAL_READER», «EXTERNAL_WRITER», «PARALLEL_COPY_READER», «REJECT_WRITER», «ЗАПИСИ»|  
|status|**nvarchar(32)**|Состояние исполнителя DMS.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|bytes_per_sec|**bigint**|Чтение или запись пропускную способность за последнюю секунду.|Больше или равно 0. Имеет значение NULL, если запрос был отменен, или не удалось выполнить, прежде чем выполнить рабочей роли.|  
|bytes_processed|**bigint**|Общее число байтов, обработанных этим исполнителем.|Больше или равно 0. Имеет значение NULL, если запрос был отменен, или не удалось выполнить, прежде чем выполнить рабочей роли.|  
|rows_processed|**bigint**|Количество строк, считываются или записываются для этого исполнителя.|Больше или равно 0. Имеет значение NULL, если запрос был отменен, или не удалось выполнить, прежде чем выполнить рабочей роли.|  
|start_time|**datetime**|Время начала выполнения этого исполнителя.|Больше или равно для запуска этапа запроса, к которому принадлежит этот рабочий процесс. См. в разделе [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Время, по которому выполнение завершено, ошибкой или был отменен.|Значение NULL для текущих или в очереди рабочих ролей. В противном случае — больше, чем start_time.|  
|total_elapsed_time|**int**|Общее время, затраченное на выполнение, в миллисекундах.|Больше или равно 0.<br /><br /> Общее время, истекшее с момента системы, запуска или перезапуска. Если total_elapsed_time превышает максимальное значение для целого числа (24,8 дня в миллисекундах), он вызывает ошибку материализации из-за переполнения.<br /><br /> Максимальное значение в миллисекундах соответствует 24,8 дня.|  
|cpu_time|**bigint**|Время ЦП, затраченное этого исполнителя в миллисекундах.|Больше или равно 0.|  
|query_time|**int**|Период времени до SQL начинается, возвращая строки в поток, в миллисекундах.|Больше или равно 0.|  
|buffers_available|**int**|Число неиспользуемых буферов.| Имеет значение NULL, если запрос был отменен, или не удалось выполнить, прежде чем выполнить рабочей роли.|  
|sql_spid|**int**|Идентификатор сеанса в экземпляре SQL Server, выполняя работу для этого исполнителя DMS.||  
|dms_cpid|**int**|Идентификатор процесса это фактический поток, в котором выполняется.||  
|error_id|**nvarchar(36)**|Уникальный идентификатор ошибки, возникшей во время выполнения этого исполнителя, если таковые имеются.|См. в разделе error_id в [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|source_info|**nvarchar(4000)**|Для чтения, спецификацию исходных таблиц и столбцов.||  
|destination_info|**nvarchar(4000)**|Для записи спецификации целевых таблиц.||  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе метаданных в [ограничения емкости](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) разделе...  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
