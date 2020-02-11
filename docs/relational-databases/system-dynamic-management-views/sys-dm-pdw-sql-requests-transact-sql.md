---
title: sys. dm_pdw_sql_requests (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 44e19609-902c-46cf-acdf-19ea75011365
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: bca9930ef51de28c8059223c93ea0bb2651f971d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68089149"
---
# <a name="sysdm_pdw_sql_requests-transact-sql"></a>sys. dm_pdw_sql_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения обо всех SQL Server распределениях запросов в рамках шага SQL в запросе.  
  
|Имя столбца|Тип данных|Description|Диапазонный индекс|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar (32)**|Уникальный идентификатор запроса, которому принадлежит данное распределение SQL запроса.<br /><br /> request_id, step_index и distribution_id образуют ключ для этого представления.|См. раздел request_id в [sys. dm_pdw_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Индекс шага запроса, частью которого является это распространение.<br /><br /> request_id, step_index и distribution_id образуют ключ для этого представления.|См. раздел step_index в [sys. dm_pdw_request_steps &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|pdw_node_id|**int**|Уникальный идентификатор узла, на котором выполняется распределение запросов.|См. раздел node_id в [sys. dm_pdw_nodes &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|distribution_id|**int**|Уникальный идентификатор распределения, на котором выполняется распределение запросов.<br /><br /> request_id, step_index и distribution_id образуют ключ для этого представления.|См. раздел distribution_id в [sys. pdw_distributions &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md). Задайте значение-1 для запросов, выполняемых в области узла, а не в области распространения.|  
|status|**nvarchar (32)**|Текущее состояние распределения запросов.|Ожидание, выполнение, сбой, отменено, завершено, прервано, Канцелсубмиттед|  
|error_id|**nvarchar (36)**|Уникальный идентификатор ошибки, связанной с этим распределением запросов, если таковые имеются.|См. раздел error_id в [sys. dm_pdw_errors &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). Если ошибка не возникала, задайте значение NULL.|  
|start_time|**datetime**|Время начала выполнения распределения запросов.|Меньше или равно текущему времени и больше или равно start_time шага запроса, к которому относится это распределение запросов|  
|end_time|**datetime**|Время, когда распределение запроса завершило выполнение, было отменено или завершилось сбоем.|Больше или равно времени начала или имеет значение NULL, если распределение запроса выполняется или помещается в очередь.|  
|total_elapsed_time|**int**|Представляет время выполнения распределения запросов в миллисекундах.|Больше или равно 0. Равно Дельта start_time и end_time для завершенных, неудачных или отмененных распределений запросов.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будет продолжать быть максимальным значением. Это условие выдаст предупреждение "превышено максимальное значение".<br /><br /> Максимальное значение в миллисекундах эквивалентно 24,8 дням.|  
|row_count|**bigint**|Число строк, измененных или считанных этим распределением запросов.|-1 для операций, которые не изменяют или возвращают данные, такие как CREATE TABLE и DROP TABLE.|  
|spid|**int**|Идентификатор сеанса на SQL Serverном экземпляре, выполняющем распределение запросов.||  
|command|**nvarchar (4000)**|Полный текст команды для этого распределения запросов.|Любой допустимый запрос или строка запроса.|  
  
 Сведения о максимальном объеме строк, хранящихся в этом представлении, см. в разделе метаданные статьи [ограничения емкости](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
