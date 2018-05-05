---
title: sys.dm_pdw_sql_requests (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 44e19609-902c-46cf-acdf-19ea75011365
caps.latest.revision: 10
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 381f23c5f72ab6e089a691850dab18b257f669be
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmpdwsqlrequests-transact-sql"></a>sys.dm_pdw_sql_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о все распределения запросов SQL Server в ходе выполнения шага SQL в запросе.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Уникальный идентификатор запроса, к которому принадлежит этот распределение запросов SQL.<br /><br /> идентификатор_запроса step_index и distribution_id формируют ключ для этого представления.|В разделе request_id в [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Индекс в очередь это распределение является частью запроса.<br /><br /> идентификатор_запроса step_index и distribution_id формируют ключ для этого представления.|В разделе step_index в [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|pdw_node_id|**int**|Уникальный идентификатор узла, на котором выполняется этот запрос распространения.|В разделе node_id в [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**int**|Уникальный идентификатор распространителя, на котором выполняется этот запрос распространения.<br /><br /> идентификатор_запроса step_index и distribution_id формируют ключ для этого представления.|В разделе distribution_id в [sys.pdw_distributions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md). Значение -1 для запросов, которые выполняются в области действия узла, не области распространения.|  
|status|**nvarchar(32)**|Текущее состояние запроса.|Ожидание "," запущена, сбоя, отмены, завершения, прервана, CancelSubmitted|  
|error_id|**nvarchar(36)**|Уникальный идентификатор ошибки, связанные с распределением этот запрос, если таковые имеются.|В разделе error_id в [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). Значение NULL, если не возникло ошибок.|  
|start_time|**datetime**|Время начала выполнения запрос распространения.|Меньше или равно значению текущего времени и больше или равно start_time этапа запроса принадлежит этот запрос распространения|  
|end_time|**datetime**|Время распространения этого запроса завершена, была отменена или сбой.|Больше или равно времени начала, или значение NULL, если распределение запросов текущей или в очереди.|  
|total_elapsed_time|**int**|Представляет время, которое выполняется распределение запросов, в миллисекундах.|Больше или равно 0. Равно дельта start_time и end_time для завершения не удалась или отменена распределения запросов.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time продолжает оставаться максимальное значение. Это условие будет создавать предупреждение «превышено максимальное значение.»<br /><br /> Максимальное значение в миллисекундах соответствует 24.8 дней.|  
|row_count|**bigint**|Число строк, изменять или считывать по распространению запроса.|-1 для операций, которые не меняют и не возвращают данные, такие как CREATE TABLE и DROP TABLE.|  
|spid|**int**|Идентификатор сеанса в экземпляре SQL Server, под управлением распределение запросов.||  
|command|**nvarchar(4000)**|Полный текст команды для распространения этого запроса.|Любое допустимое строковое выражение запроса или запроса.|  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении, обратитесь к разделу максимальные значения представление системы в [минимальное и максимальное значения (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9) раздела.  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамических административных представлений &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
