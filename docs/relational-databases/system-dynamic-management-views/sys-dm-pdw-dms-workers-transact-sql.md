---
title: sys.dm_pdw_dms_workers (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0a284d18-3c46-4ffa-bcc9-689e660ee8b4
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 68d4b12395172f8ea5c820e745abf2a3f5f4c7c8
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmpdwdmsworkers-transact-sql"></a>sys.dm_pdw_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех работников, выполнив действия DMS.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Запрос, который входит в состав этого исполнителя DMS.<br /><br /> идентификатор_запроса step_index и dms_step_index формируют ключ для этого представления.|В разделе request_id в [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Запрос шаг, который входит в состав этого исполнителя DMS.<br /><br /> идентификатор_запроса step_index и dms_step_index формируют ключ для этого представления.|В разделе step_index в [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Шаг в плане DMS, на котором выполняется этот рабочий процесс.<br /><br /> идентификатор_запроса step_index и dms_step_index формируют ключ для этого представления.||  
|pdw_node_id|**int**|Узел, на котором выполняется рабочий процесс, на.|В разделе node_id в [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**Int**|Распределение, которое исполнитель выполняется, если таковые имеются.|В разделе distribution_id в [sys.pdw_distributions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md).|  
|Тип|**nvarchar(32)**|Тип DMS рабочий поток, который представляет эта запись.|«DIRECT_CONVERTER», «DIRECT_READER», «FILE_READER», «HASH_CONVERTER», «HASH_READER», «ROUNDROBIN_CONVERTER», «EXPORT_READER», «EXTERNAL_READER», «EXTERNAL_WRITER», «PARALLEL_COPY_READER», «REJECT_WRITER», «ЗАПИСИ»|  
|status|**nvarchar(32)**|Состояние рабочего процесса DMS.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|bytes_per_sec|**bigint**|Чтение или запись пропускной способности в течение последней секунды.|Больше или равно 0. Имеет значение NULL, если запрос был отменен или не удалось выполнить, прежде чем выполнить рабочий процесс.|  
|bytes_processed|**bigint**|Общее количество байт, обработанных этим исполнителем.|Больше или равно 0. Имеет значение NULL, если запрос был отменен или не удалось выполнить, прежде чем выполнить рабочий процесс.|  
|rows_processed|**bigint**|Число строк, чтение и запись для этого исполнителя.|Больше или равно 0. Имеет значение NULL, если запрос был отменен или не удалось выполнить, прежде чем выполнить рабочий процесс.|  
|start_time|**datetime**|Время начала выполнения этого исполнителя.|Больше или равно во время этапа запроса, к которому принадлежит этот рабочий процесс запуска. В разделе [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Время, когда выполнение завершено, ошибкой или был отменен.|Значение NULL для текущей или в очереди рабочих процессов. В противном случае — больше, чем start_time.|  
|total_elapsed_time|**int**|Общее время, затраченное на выполнение, в миллисекундах.|Больше или равно 0.<br /><br /> Общее время, истекшее с момента системы запуска или перезапуска. Если total_elapsed_time превышает максимальное значение для целого числа (24.8 дней в миллисекундах), это приведет к переполнению материализации сбой из-за.<br /><br /> Максимальное значение в миллисекундах соответствует 24.8 дней.|  
|cpu_time|**bigint**|Время ЦП, использованное этого исполнителя в миллисекундах.|Больше или равно 0.|  
|query_time|**int**|Период времени, прежде чем SQL начинается возврат строк в поток, в миллисекундах.|Больше или равно 0.|  
|buffers_available|**int**|Число неиспользуемых буферов.| Имеет значение NULL, если запрос был отменен или не удалось выполнить, прежде чем выполнить рабочий процесс.|  
|sql_spid|**int**|Идентификатор сеанса в экземпляре SQL Server, выполнять работу для этого исполнителя DMS.||  
|dms_cpid|**int**|Идентификатор процесса фактическое выполнение потока.||  
|error_id|**nvarchar(36)**|Уникальный идентификатор ошибки, возникшей во время выполнения этого исполнителя, если таковые имеются.|В разделе error_id в [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|source_info|**nvarchar(4000)**|Для чтения, спецификация исходных таблиц и столбцов.||  
|destination_info|**nvarchar(4000)**|Для модуля записи спецификации целевых таблиц.||  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе [максимальные значения представление системы](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9).  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамических административных представлений &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
