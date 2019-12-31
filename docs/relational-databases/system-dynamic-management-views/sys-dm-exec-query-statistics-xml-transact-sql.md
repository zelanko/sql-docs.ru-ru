---
title: sys. dm_exec_query_statistics_xml (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: 35f9cdfcc40d417a6aed19a3abe0e590061b2eb7
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75256011"
---
# <a name="sysdm_exec_query_statistics_xml-transact-sql"></a>sys. dm_exec_query_statistics_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Возвращает план выполнения запроса для запросов в реальном режиме. Используйте это динамическое административное представление для получения XML-документа Showplan с временной статистикой. 

## <a name="syntax"></a>Синтаксис

```
sys.dm_exec_query_statistics_xml(session_id)  
``` 

## <a name="arguments"></a>Аргументы 
*session_id*  
 Идентификатор сеанса, в котором будет выполняться поиск пакета. *session_id* имеет **smallint**. *session_id* можно получить из следующих объектов DMO:  
  
-   [sys. dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys. dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys. dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  

## <a name="table-returned"></a>Возвращаемая таблица

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|
|session_id|**smallint**|Идентификатор сеанса. Не допускает значения NULL.|
|request_id|**int**|Идентификатор запроса. Не допускает значения NULL.|
|sql_handle|**varbinary (64)**|Токен, однозначно определяющий пакет или хранимую процедуру, частью которой является запрос. Допускает значение NULL.|
|plan_handle|**varbinary (64)**|Токен, однозначно определяющий план выполнения запроса для выполняемого в данный момент пакета. Допускает значение NULL.|
|query_plan|**Xml**|Содержит представление среды выполнения Showplan плана выполнения запроса, указанного в *plan_handle* содержащего частичную статистику. Представление Showplan имеет формат XML. Для каждого пакета, содержащего, например нерегламентированные инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], вызовы хранимых процедур и вызовы определяемых пользователем функций, формируется один план. Допускает значение NULL.|

## <a name="remarks"></a>Замечания
Эта системная функция доступна начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] версии с пакетом обновления 1 (SP1). См. статью KB [3190871](https://support.microsoft.com/help/3190871)

Эта системная функция работает как в **стандартной** и **упрощенной** инфраструктуре профилирования статистики выполнения запросов. Дополнительные сведения см. в разделе [инфраструктура профилирования запросов](../../relational-databases/performance/query-profiling-infrastructure.md).  

В следующих случаях выходные данные Showplan не возвращаются в столбце **query_plan** возвращаемой таблицы для **sys. dm_exec_query_statistics_xml**.  
  
-   Если план запроса, соответствующий указанному *session_id* , больше не исполняется, **query_plan** столбец возвращаемой таблицы имеет значение null. Например, это условие может возникать, если задержка между моментом записи обработчика плана и ее использованием с представлением **sys. dm_exec_query_statistics_xml**.  
    
Из-за ограничения количества вложенных уровней, разрешенных в типе данных **XML** , **sys. dm_exec_query_statistics_xml** не может возвращать планы запросов, которые соответствуют или превышают 128 уровней вложенных элементов. В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это условие предназначалось для предотвращения возврата плана запроса и формирования ошибки 6335. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] пакетах обновления 2 (SP2) и более поздних версиях столбец **query_plan** возвращает значение null.   

## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  

## <a name="examples"></a>Примеры  
  
### <a name="a-looking-at-live-query-plan-and-execution-statistics-for-a-running-batch"></a>а. Просмотр динамического плана запроса и статистики выполнения для выполняемого пакета  
 В следующем примере запрашиваются **sys. dm_exec_requests** , чтобы найти интересный запрос и `session_id` скопировать его из выходных данных.  
  
```sql  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 Затем, чтобы получить динамический план запроса и статистику выполнения, используйте скопированную `session_id` с помощью системной функции **sys. dm_exec_query_statistics_xml**.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_query_statistics_xml(< copied session_id >);  
GO  
```   

 Или в сочетании для всех выполняющихся запросов.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_requests
CROSS APPLY sys.dm_exec_query_statistics_xml(session_id);  
GO  
```   
  
## <a name="see-also"></a>См. также
  [Флаги трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Динамические административные представления и функции &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с базами данных &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

