---
title: "sys.dm_exec_distributed_requests (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_REQUESTS
- DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- sys.dm_exec_distributed_sql_requests management view
- PolyBase
- dm_exec_distributed_sql_requests management view
ms.assetid: c041d416-d8c6-435e-a563-6a310abd33e3
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 539bf6f6e4df5860977fdd0703a9bc11a5923d31
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecdistributedrequests-transact-sql"></a>sys.dm_exec_distributed_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех запросов в настоящее время или недавно активен в запросы PolyBase. Он содержит одну строку для каждого запроса или запрос.  
  
 В зависимости от сеанса и запросить идентификатор, пользователь может найти фактический распределенных запросов, созданных для выполнения — через sys.dm_exec_distributed_requests. Например запрос, включающий регулярное SQL и внешних таблиц SQL будет разложить на различных инструкций и запросов, выполняемых на различных вычислительных узлах. Для отслеживания распределенной действия на всех узлах вычислений, мы представляем идентификатор «global» выполнения, который можно использовать для отслеживания всех операций на вычислительные узлы, связанные с одного конкретного запроса и оператора, соответственно.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|sql_handle|**varbinary(64)**|Ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|Уникален в пределах всех запросов в системе.|  
|execution_id|**nvarchar(32**|Уникальный числовой идентификатор, связанный с сеансом, в котором был запущен этот запрос.||  
|status|**nvarchar(32**|Текущее состояние запроса.|'Pending', 'Authorizing', 'AcquireSystemResources', 'Initializing', 'Plan', 'Parsing', 'AquireResources', 'Running', 'Cancelling', 'Complete', 'Failed', 'Cancelled'.|  
|error_id|**nvarchar(36)**|Уникальный идентификатор ошибки, связанные с запросом, если таковые имеются.|Значение NULL, если не возникло ошибок.|  
|start_time|**datetime**|Время начала выполнения запроса.|0 для запросов в очереди; в противном случае — допустимое Дата и время меньше или равно значению текущего времени.|  
|end_time|**datetime**|Время, обработчик завершения компиляции запроса.|Значение NULL для запросов в очереди или активный. в противном случае действительное значение datetime, меньше или равно значению текущего времени.|  
|total_elapsed_time|**int**|Затраченное время на выполнение с момента запуска запроса в миллисекундах.|Между 0 и разницу между start_time и end_time. Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time продолжает оставаться максимальное значение. Это условие будет создавать предупреждение «превышено максимальное значение.» Максимальное значение в миллисекундах соответствует 24.8 дней.|  
  
## <a name="see-also"></a>См. также  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления &#40; относящиеся к базе данных Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
