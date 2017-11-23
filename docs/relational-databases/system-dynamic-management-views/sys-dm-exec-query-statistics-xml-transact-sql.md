---
title: "sys.dm_exec_query_statistics_xml (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.dm_exec_query_statistics_xml
- sys.dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml
helpviewer_keywords: sys.dm_exec_query_statistics_xml management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfecb
caps.latest.revision: "6"
author: pmasl
ms.author: pelopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 051b93348547603d2e68a007ede531bfa73a6d58
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecquerystatisticsxml-transact-sql"></a>sys.dm_exec_query_statistics_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Возвращает выполнения план запроса для активных запросов. Используйте это динамическое административное Представление для получения showplan XML с временной статистики. 

## <a name="syntax"></a>Синтаксис

```
sys.dm_exec_query_statistics_xml(session_id)  
``` 

## <a name="arguments"></a>Аргументы 
*session_id*  
 Идентификатор сеанса, выполняет поиск пакета. *session_id* — **smallint**. *session_id* можно получить из следующих объектов DMO:  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  

## <a name="table-returned"></a>Возвращаемая таблица
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|
|session_id|**smallint**|Идентификатор сеанса. Не допускает значения NULL.|
|request_id|**int**|Идентификатор запроса. Не допускает значения NULL.|
|sql_handle|**varbinary(64)**|Карта хэширования SQL-текста запроса. Допускает значение NULL.|
|plan_handle|**varbinary(64)**|Хэш-карта плана запроса. Допускает значение NULL.|
|query_plan|**xml**|Showplan XML с частичной статистики. Допускает значение NULL.|

## <a name="remarks"></a>Замечания
Эта функция доступна, начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1.

Эта функция работает как в **Стандартная** и **упрощенных** инфраструктуры профилирования статистику выполнения запросов.  
  
**Стандартная** статистики инфраструктуры профилирования можно включить с помощью:
  -  [SET STATISTICS XML НА](../../t-sql/statements/set-statistics-xml-transact-sql.md)
  -  [SET STATISTICS PROFILE НА](../../t-sql/statements/set-statistics-profile-transact-sql.md)
  -  `query_post_execution_showplan` расширенных событий.  
  
**Упрощенный** статистики инфраструктуры профилирования доступна в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и может быть включен:
  -  Глобально с помощью трассировки флаг 7412.
  -  С помощью [ *query_thread_profile* ](http://support.microsoft.com/kb/3170113) расширенных событий.
  
> [!NOTE]
> После включения флага трассировки 7412 упрощенных профилирование будет разбит на любой потребитель статистику выполнения запросов, профилирование инфраструктуры вместо обычного профилирования, таких как динамическое административное Представление [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md).
> Однако обычного профилирования по-прежнему используется для инструкции SET STATISTICS XML, *Включить действительный план* действия в [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)], и `query_post_execution_showplan` xEvent.

> [!IMPORTANT]
> В TPC-C, как рабочая нагрузка Включение профилирования инфраструктуру статистики упрощенных добавляет издержки 1,5 до 2 процентов. Напротив инфраструктуру стандартные статистики профилирования можно добавить до 90 процентов затраты для того же сценарий рабочей нагрузки.

## <a name="permissions"></a>Permissions  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  

## <a name="examples"></a>Примеры  
  
### <a name="a-looking-at-live-query-plan-and-execution-statistics-for-a-running-batch"></a>A. Просмотр динамических запросов плана и Статистика выполнения для выполнения пакета  
 В следующем примере запрос **sys.dm_exec_requests** для поиска необходимого запроса и копирования его `session_id` из выходных данных.  
  
```t-sql  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 Затем, чтобы получить динамическую планирования и выполнения статистику запросов, использовать скопированный `session_id` с помощью системной функции **sys.dm_exec_query_statistics_xml**.  
  
```t-sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_query_statistics_xml(< copied session_id >);  
GO  
```   

 Или их комбинация для всех запущенных запросов.  
  
```t-sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_requests
CROSS APPLY sys.dm_exec_query_statistics_xml(session_id);  
GO  
```   
  
## <a name="see-also"></a>См. также:
  [Флаги трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления &#40; относящиеся к базе данных Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

