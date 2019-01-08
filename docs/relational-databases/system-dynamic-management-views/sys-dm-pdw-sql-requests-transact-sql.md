---
title: sys.dm_pdw_sql_requests (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 44e19609-902c-46cf-acdf-19ea75011365
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 71fee8fa84355217ca7cf3099272c4cf2aa8a487
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52397597"
---
# <a name="sysdmpdwsqlrequests-transact-sql"></a>sys.dm_pdw_sql_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех дистрибутивов запроса SQL Server как часть действия SQL в запросе.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Уникальный идентификатор запроса, к которой принадлежит это распределение запросов SQL.<br /><br /> Идентификатор request_id step_index и идентификатор distribution_id формируют ключ для этого представления.|См. в разделе request_id в [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Индекс, это распределение является частью этапа запроса.<br /><br /> Идентификатор request_id step_index и идентификатор distribution_id формируют ключ для этого представления.|См. в разделе step_index в [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|pdw_node_id|**int**|Уникальный идентификатор узла, на котором выполняется этот запрос распространения.|См. в разделе node_id в [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**int**|Уникальный идентификатор распределения, на котором выполняется этот запрос распространения.<br /><br /> Идентификатор request_id step_index и идентификатор distribution_id формируют ключ для этого представления.|См. в разделе идентификатор distribution_id в [sys.pdw_distributions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md). Значение -1 для запросов, выполняемых на уровне узла не области распространения.|  
|status|**nvarchar(32)**|Текущее состояние распределения запросов.|Ожидание под управлением, не удалось выполнить, отменено, завершено, прервана, CancelSubmitted|  
|error_id|**nvarchar(36)**|Уникальный идентификатор для ошибки, связанные с этой распределение запросов при наличии.|См. в разделе error_id в [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). Значение NULL, если не возникло ошибок.|  
|start_time|**datetime**|Время начала выполнения какой запрос распространения.|Меньше или равно текущего времени и больше или равно start_time шага запрос принадлежит это распределение запросов|  
|end_time|**datetime**|Время, по которому это распределение запросов завершил выполнение, была отменена или не удалось.|Больше или равно времени начала, или значение NULL, если распределение запросов текущей или в очереди.|  
|total_elapsed_time|**int**|Представляет время, которое работает распределение запросов, в миллисекундах.|Больше или равно 0. Равные дельта start_time и end_time для завершения, отменена или завершилась сбоем распределения запросов.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будут продолжать максимальное значение. Это условие будет создавать предупреждение «превышено максимальное значение.»<br /><br /> Максимальное значение в миллисекундах соответствует 24,8 дня.|  
|row_count|**bigint**|Количество строк, изменить или считываемые этой распределение запросов.|-1 для операций, которые не меняют и не возвращают данные, такие как CREATE TABLE и DROP TABLE.|  
|spid|**int**|Идентификатор сеанса в экземпляре SQL Server, под управлением дистрибутива запроса.||  
|command|**nvarchar(4000)**|Полный текст команды для распространения этого запроса.|Любая допустимая строка, запрос или запрос.|  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе максимальные значения представление системы в [минимальное и максимальное значения (SQL Server PDW)](https://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9) раздела.  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
