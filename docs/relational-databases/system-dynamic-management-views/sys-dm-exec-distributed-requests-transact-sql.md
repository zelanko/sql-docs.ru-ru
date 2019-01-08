---
title: sys.dm_exec_distributed_requests (Transact-SQL) | Документация Майкрософт
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 78604c723c4c19e68a6c29fd3113de3d69d36d44
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52532787"
---
# <a name="sysdmexecdistributedrequests-transact-sql"></a>sys.dm_exec_distributed_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех запросов в настоящее время или недавно active в запросы PolyBase. В ней перечислены одну строку для каждого запроса или запроса.  
  
 На основании сеанса и идентификатор, запроса пользователь может извлечь фактические распределенные запросы, созданные для выполнения — через sys.dm_exec_distributed_requests. Например запрос, включающий регулярных SQL и внешних таблиц SQL будет разложить на различных инструкций и запросов, выполняемых на различные вычислительные узлы. Для отслеживания распределенной шаги на всех вычислительных узлах, мы представляем идентификатор «global» выполнения, который может использоваться для отслеживания всех операций в вычислительные узлы, связанные с помощью одного конкретного запроса и оператора, соответственно.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|sql_handle|**varbinary(64)**|Ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|Уникально для всех запросов в системе.|  
|execution_id|**nvarchar (32**|Уникальный числовой идентификатор, связанный с сеансом, в котором был запущен этот запрос.||  
|status|**nvarchar (32**|Текущее состояние запроса.|«Ожидание» «Авторизация», «AcquireSystemResources», «Инициализация», «План», «Анализ», «AquireResources», «Работает», «Отмена», «Завершено», «сбой», «Отменено».|  
|error_id|**nvarchar(36)**|Уникальный идентификатор ошибку, связанную с запросом, если таковые имеются.|Значение NULL, если не возникло ошибок.|  
|start_time|**datetime**|Время начала выполнения запроса.|0 для запросов в очереди; в противном случае — допустимые даты и времени меньше или равна текущее время.|  
|end_time|**datetime**|Время, обработчик завершения компиляции запроса.|Значение NULL для запросов в очереди, либо active; в противном случае допустимые дату и время, меньшее или равное текущее время.|  
|total_elapsed_time|**int**|Время затраченное на выполнение с момента запуска запроса, в миллисекундах.|Между 0 и разница между start_time и end_time. Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будут продолжать максимальное значение. Это условие будет создавать предупреждение «превышено максимальное значение.» Максимальное значение в миллисекундах соответствует 24,8 дня.|  
  
## <a name="see-also"></a>См. также  
 [PolyBase, устранение неполадок с помощью динамических административных представлений](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
