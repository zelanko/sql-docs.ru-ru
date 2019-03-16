---
title: sys.dm_exec_query_statistics_xml (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_statistics_xml
- sys.dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml
helpviewer_keywords:
- sys.dm_exec_query_statistics_xml management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfecb
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 63e1d22670929448110083c31e9900e462d576bc
ms.sourcegitcommit: 671370ec2d49ed0159a418b9c9ac56acf43249ad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072308"
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
 Идентификатор сеанса выполнения пакета выполняется поиск. *session_id* — **smallint**. *session_id* можно получить из следующих объектов DMO:  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  

## <a name="table-returned"></a>Возвращаемая таблица

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|
|session_id|**smallint**|Идентификатор сеанса. Не допускает значения NULL.|
|request_id|**int**|Идентификатор запроса. Не допускает значения NULL.|
|sql_handle|**varbinary(64)**|Карта хэширования SQL-текста запроса. Допускает значение NULL.|
|plan_handle|**varbinary(64)**|Карта хэширования плана запроса. Допускает значение NULL.|
|query_plan|**xml**|Showplan XML с частичной статистики. Допускает значение NULL.|

## <a name="remarks"></a>Примечания
Этой системной функции доступен, начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1. См. в статье базы Знаний [3190871](https://support.microsoft.com/en-us/help/3190871)

Это системная функция работает при обоих **стандартный** и **упрощенных** инфраструктуру профилирования статистики выполнения запросов. Дополнительные сведения см. в разделе [Инфраструктура профилирования запросов](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md).  

## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  

## <a name="examples"></a>Примеры  
  
### <a name="a-looking-at-live-query-plan-and-execution-statistics-for-a-running-batch"></a>A. Просмотрев активных запросов плана и Статистика выполнения для выполнения пакета  
 В следующем примере запрос **sys.dm_exec_requests** для поиска необходимого запроса и копирования его `session_id` из выходных данных.  
  
```sql  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 Затем, чтобы получить динамическую план и выполнения статистику запросов, использовать скопированный `session_id` с помощью системной функции **sys.dm_exec_query_statistics_xml**.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_query_statistics_xml(< copied session_id >);  
GO  
```   

 Или их комбинация для всех выполняющихся запросов.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_requests
CROSS APPLY sys.dm_exec_query_statistics_xml(session_id);  
GO  
```   
  
## <a name="see-also"></a>См. также
  [Флаги трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

