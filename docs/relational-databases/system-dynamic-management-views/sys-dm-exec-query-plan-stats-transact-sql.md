---
title: sys.dm_exec_query_plan_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/23/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_plan_stats
- sys.dm_exec_query_plan_stats_TSQL
- dm_exec_query_plan_stats_TSQL
- dm_exec_query_plan_stats
helpviewer_keywords:
- sys.dm_exec_query_plan_stats management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfacb
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: 89185976120c15f9d1fcdfef75f2bddb41415c65
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63474280"
---
# <a name="sysdmexecqueryplanstats-transact-sql"></a>sys.dm_exec_query_plan_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-asdb-xxxx-xxx.md)]

Возвращает эквивалент последнего известного фактический план выполнения для ранее кэшированного плана запроса. 

## <a name="syntax"></a>Синтаксис

```
sys.dm_exec_query_plan_stats(plan_handle)  
``` 

## <a name="arguments"></a>Аргументы 
*plan_handle*  
— Это маркер, который уникально идентифицирует план выполнения запроса для запущенного пакета, и ее план находится в кэше планов, или в данный момент. *plan_handle* — **varbinary(64)**.   

*Plan_handle* можно получить из следующих объектов DMO:  
  
-   [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  

## <a name="table-returned"></a>Возвращаемая таблица

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|
|**dbid**|**smallint**|Идентификатор базы данных, в контексте которой выполнялась компиляция инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], соответствующей данному плану. Для нерегламентированных и подготовленных инструкций SQL это идентификатор базы данных, в которой происходила компиляция инструкции.<br /><br /> Столбец может содержать значение NULL.|  
|**objectid**|**int**|Идентификатор объекта (например хранимой процедуры или определяемой пользователем функции) для этого плана запроса. Для нерегламентированных и подготовленных пакетов этот столбец содержит **null**.<br /><br /> Столбец может содержать значение NULL.|  
|**number**|**smallint**|Целое число нумерованных хранимых процедур. Например, группа процедур для **заказы** приложения может называться **orderproc; 1**, **orderproc; 2**, и т. д. Для нерегламентированных и подготовленных пакетов этот столбец содержит **null**.<br /><br /> Столбец может содержать значение NULL.|  
|**Шифрование**|**bit**|Указывает, зашифрована ли соответствующая хранимая процедура.<br /><br /> 0 = не зашифрована<br /><br /> 1 = зашифрована<br /><br /> Столбец не может содержать значение NULL.|  
|**query_plan**|**xml**|Содержит последние известные среды выполнения представление Showplan фактический план выполнения запроса, указанный с помощью *plan_handle*. Представление Showplan имеет формат XML. Для каждого пакета, содержащего, например нерегламентированные инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], вызовы хранимых процедур и вызовы определяемых пользователем функций, формируется один план.<br /><br /> Столбец может содержать значение NULL.| 

## <a name="remarks"></a>Примечания
Этой системной функции доступен, начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.4.

Эта функция активируется явным образом и требует включения [флага трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451. Начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP-версии 2.5 и в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], для выполнения этой задачи на уровне базы данных, см. в описании параметра LAST_QUERY_PLAN_STATS в [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

Эта функция системы, работает под **упрощенных** инфраструктуру профилирования статистики выполнения запросов. Дополнительные сведения см. в разделе [Инфраструктура профилирования запросов](../../relational-databases/performance/query-profiling-infrastructure.md).  

При следующих условиях вывод инструкции Showplan **эквивалентно фактический план выполнения** возвращается в **query_plan** столбец возвращаемой таблицы для **sys.dm_exec_query_plan_ Статистика**:  

-   План можно найти в [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md).     
    **AND**    
-   Выполняемый запрос является сложных или потребления ресурсов.

При следующих условиях **упрощенный <sup>1</sup>**  выходных данных Showplan возвращается в **query_plan** столбец возвращаемой таблицы для **sys.dm_exec_ query_plan_stats**:  

-   План можно найти в [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md).     
    **AND**    
-   Запрос является довольно простой, обычно относится к категории как часть рабочей нагрузки OLTP.

<sup>1</sup> начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP-версии 2.5, это относится к инструкции Showplan, который содержит только узел оператор задания корневого каталога (SELECT). Для [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.4, это относится к кэшированного плана по мере доступности через `sys.dm_exec_cached_plans`.

При следующих условиях **вывод не возвращается** из **sys.dm_exec_query_plan_stats**:

-   План запроса, который указан с помощью *plan_handle* исключен из кэша планов.     
    **OR**    
-   План запроса в первую очередь не может быть кэширован. Дополнительные сведения см. в разделе [кэширование и плана выполнения повторного использования ](../../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse).
  
> [!NOTE] 
> Из-за ограничения количества уровней вложенности, допустимых в **xml** тип данных, **sys.dm_exec_query_plan** не может возвратить планы запросов, которые соответствуют или превосходят 128 уровней вложенных элементов. В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], это условие предназначалось для предотвращения возврата плана запроса и [формирования ошибки 6335](../../relational-databases/errors-events/database-engine-events-and-errors.md#errors-6000-to-6999). В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 и более поздних версиях **query_plan** столбец возвращает значение NULL.  

## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  

## <a name="examples"></a>Примеры  
  
### <a name="a-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan"></a>A. Ищете наконец известных фактический план выполнения запроса определенного кэшированного плана  
 В следующем примере запрос **sys.dm_exec_cached_plans** для поиска необходимого плана и копирования его `plan_handle` из выходных данных.  
  
```sql  
SELECT * FROM sys.dm_exec_cached_plans;  
GO  
```  
  
Затем, чтобы получить последние известные фактический план выполнения запроса, используйте скопированный `plan_handle` с помощью системной функции **sys.dm_exec_query_plan_stats**.  
  
```sql  
SELECT * FROM sys.dm_exec_query_plan_stats(< copied plan_handle >);  
GO  
```   

### <a name="b-looking-at-last-known-actual-query-execution-plan-for-all-cached-plans"></a>Б. Ищете наконец известных фактический план выполнения запроса всех кэшированных планов
  
```sql  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle) AS qps;  
GO  
```   

### <a name="c-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan-and-query-text"></a>В. Ищете наконец известных фактический план выполнения запроса определенного кэшированного плана и текста запроса

```sql  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle) AS qps
WHERE st.text LIKE 'SELECT * FROM Person.Person%';  
GO  
```   

### <a name="d-look-at-cached-events-for-trigger"></a>Г. Рассмотрим кэшированных событий для триггера

```sql
SELECT *
FROM sys.dm_exec_cached_plans
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle)
WHERE objtype ='Trigger';
GO
```

## <a name="see-also"></a>См. также
  [Флаги трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  

