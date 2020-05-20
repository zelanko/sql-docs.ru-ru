---
title: sys. dm_exec_distributed_requests (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 52a1ee453d0a516bc2dc1fd42dcd4439272d844c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821155"
---
# <a name="sysdm_exec_distributed_requests-transact-sql"></a>sys. dm_exec_distributed_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит сведения обо всех запросах, которые в данный момент или недавно были активны в запросах Polybase. В нем отображается одна строка для каждого запроса или запроса.  
  
 В зависимости от идентификатора сеанса и запроса пользователь может получить фактически распределенные запросы, созданные для выполнения, с помощью sys. dm_exec_distributed_requests. Например, запрос, включающий обычные SQL и внешние таблицы SQL, будет разноситься в различные инструкции и запросы, выполняемые на различных узлах вычислений. Для трассировки распределенных шагов на всех вычислительных узлах мы представляем глобальный идентификатор выполнения, который можно использовать для трассировки всех операций на вычислительных узлах, связанных с одним конкретным запросом и оператором соответственно.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|sql_handle|**varbinary (64)**|Ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|Уникальный для всех запросов в системе.|  
|execution_id|**nvarchar (32**|Уникальный числовой идентификатор, связанный с сеансом, в котором выполнялся этот запрос.||  
|status|**nvarchar (32**|Текущее состояние запроса.|"Pending", "Авторизация", "Аккуиресистемресаурцес", "Инициализация", "Plan", "анализ", "Акуирересаурцес", "выполняется", "Отмена", "завершение", "сбой", "отменено".|  
|error_id|**nvarchar (36)**|Уникальный идентификатор ошибки, связанной с запросом, если он есть.|Если ошибка не возникала, задайте значение NULL.|  
|start_time|**datetime**|Время начала выполнения запроса.|0 для запросов в очереди; в противном случае допустимое значение DateTime меньше или равно текущему времени.|  
|end_time|**datetime**|Время, когда обработчик завершил компиляцию запроса.|Значение NULL для очереди или активных запросов; в противном случае допустимое значение DateTime меньше или равно текущему времени.|  
|total_elapsed_time|**int**|Время, затраченное на выполнение с момента запуска запроса, в миллисекундах.|Между 0 и разностью между start_time и end_time. Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будет продолжать быть максимальным значением. Это условие выдаст предупреждение "превышено максимальное значение". Максимальное значение в миллисекундах эквивалентно 24,8 дням.|  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок в Polybase с помощью динамических административных представлений](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с базами данных &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
