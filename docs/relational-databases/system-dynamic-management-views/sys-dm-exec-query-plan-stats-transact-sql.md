---
title: sys. dm_exec_query_plan_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/22/2019
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
ms.openlocfilehash: 279f1a8fbe3ec78dc0cae30d9879615b169075bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75656996"
---
# <a name="sysdm_exec_query_plan_stats-transact-sql"></a>sys. dm_exec_query_plan_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-asdb-xxxx-xxx.md)]

Возвращает эквивалент последнего известного реального плана выполнения для ранее кэшированного плана запроса.

## <a name="syntax"></a>Синтаксис

```
sys.dm_exec_query_plan_stats(plan_handle)  
``` 

## <a name="arguments"></a>Аргументы 
*plan_handle*  
Токен, однозначно определяющий план выполнения запроса для пакета, который был выполнен, а его план находится в кэше планов или в данный момент выполняется. *plan_handle* имеет тип **varbinary (64)**.   

*Plan_handle* можно получить из следующих объектов DMO:  
  
-   [sys. dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys. dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys. dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys. dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys. dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  

## <a name="table-returned"></a>Возвращаемая таблица

|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|
|**DBID**|**smallint**|Идентификатор базы данных, в контексте которой выполнялась компиляция инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], соответствующей данному плану. Для нерегламентированных и подготовленных инструкций SQL это идентификатор базы данных, в которой происходила компиляция инструкции.<br /><br /> Столбец может содержать значение NULL.|  
|**ИД**|**int**|Идентификатор объекта (например хранимой процедуры или определяемой пользователем функции) для этого плана запроса. Для нерегламентированных и подготовленных пакетов этот столбец содержит значение **NULL**.<br /><br /> Столбец может содержать значение NULL.|  
|**number**|**smallint**|Целое число нумерованных хранимых процедур. Например, группа процедур для приложения **orders** может иметь имена вида **orderproc;1**, **orderproc;2** и так далее. Для нерегламентированных и подготовленных пакетов этот столбец содержит значение **NULL**.<br /><br /> Столбец может содержать значение NULL.|  
|**Шифрование**|**bit**|Указывает, зашифрована ли соответствующая хранимая процедура.<br /><br /> 0 = не зашифрована<br /><br /> 1 = зашифрована<br /><br /> Столбец не может содержать значение NULL.|  
|**query_plan**|**xml**|Содержит Последнее известное представление среды выполнения Showplan о фактическом плане выполнения запроса, указанном с помощью *plan_handle*. Представление Showplan имеет формат XML. Для каждого пакета, содержащего, например нерегламентированные инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], вызовы хранимых процедур и вызовы определяемых пользователем функций, формируется один план.<br /><br /> Столбец может содержать значение NULL.| 

## <a name="remarks"></a>Remarks
Эта системная функция доступна начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] версии CTP 2,4.

Эта функция активируется явным образом и требует включения [флага трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451. Начиная с версии [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.5 эта задача выполняется на уровне базы данных в соответствии с инструкциями, которые можно найти в описании параметра LAST_QUERY_PLAN_STATS в статье [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

Эта системная функция работает в инфраструктуре профилирования статистики выполнения **упрощенных** запросов. Дополнительные сведения см. в разделе [инфраструктура профилирования запросов](../../relational-databases/performance/query-profiling-infrastructure.md).  

Выходные данные инструкции Showplan с помощью sys. dm_exec_query_plan_stats содержат следующие сведения:
-  Все сведения времени компиляции, найденные в кэшированном плане
-  Сведения о среде выполнения, такие как фактическое число строк на оператор, общее время ЦП и время выполнения запроса, сброс предупреждений, фактическое значение DOP, максимальный объем используемой памяти и предоставленная память

В следующих случаях результат инструкции Showplan, **эквивалентный фактическому плану выполнения** , возвращается в **query_plan** столбец возвращаемой таблицы для **sys. dm_exec_query_plan_stats**.  

-   Этот план можно найти в [представлении каталога sys. dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md).     
    **AND**    
-   Выполняемый запрос является сложным или потребляет ресурсы.

В следующих случаях в столбце **query_plan** возвращаемой таблицы для **sys. dm_exec_query_plan_stats**возвращается **упрощенный результат <sup>1</sup> ** Showplan.  

-   Этот план можно найти в [представлении каталога sys. dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md).     
    **AND**    
-   Запрос достаточно прост, обычно разбитый на категории в рамках рабочей нагрузки OLTP.

<sup>1</sup> начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] версии CTP 2,5 это относится к инструкции Showplan, которая содержит только оператор корневого узла (SELECT). Для [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2,4 это — кэшированный план, доступный через `sys.dm_exec_cached_plans`.

В следующих случаях выходные данные **sys. dm_exec_query_plan_stats** **не возвращаются** .

-   План запроса, указанный с помощью *plan_handle* , был исключен из кэша планов.     
    **OR**    
-   На первом месте план запроса не был кэширован. Дополнительные сведения см. в разделе [кэширование и повторное использование плана выполнения ](../../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse).
  
> [!NOTE] 
> Из-за ограничения количества вложенных уровней, разрешенных в типе данных **XML** , **sys. dm_exec_query_plan** не может возвращать планы запросов, которые соответствуют или превышают 128 уровней вложенных элементов. В более ранних [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]версиях это условие не позволило возвратить план запроса и выдает [ошибку 6335](../../relational-databases/errors-events/database-engine-events-and-errors.md#errors-6000-to-6999). В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] пакетах обновления 2 (SP2) и более поздних версиях столбец **query_plan** возвращает значение null.  

## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  

## <a name="examples"></a>Примеры  
  
### <a name="a-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan"></a>A. Просмотр последнего известного фактического плана выполнения запроса для определенного кэшированного плана  
 В следующем примере производится запрос к **sys. dm_exec_cached_plans** для поиска интересного плана и `plan_handle` копирования его из выходных данных.  
  
```sql  
SELECT * FROM sys.dm_exec_cached_plans;  
GO  
```  
  
Затем, чтобы получить последний известный план выполнения запроса, используйте скопированную `plan_handle` с помощью системной функции **sys. dm_exec_query_plan_stats**.  
  
```sql  
SELECT * FROM sys.dm_exec_query_plan_stats(< copied plan_handle >);  
GO  
```   

### <a name="b-looking-at-last-known-actual-query-execution-plan-for-all-cached-plans"></a>Б. Просмотр последнего известного плана выполнения запроса для всех кэшированных планов
  
```sql  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle) AS qps;  
GO  
```   

### <a name="c-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan-and-query-text"></a>В. Просмотр последнего известного фактического плана выполнения запроса для определенного кэшированного плана и текста запроса

```sql  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle) AS qps
WHERE st.text LIKE 'SELECT * FROM Person.Person%';  
GO  
```   

### <a name="d-look-at-cached-events-for-trigger"></a>Г. Просмотр кэшированных событий для триггера

```sql
SELECT *
FROM sys.dm_exec_cached_plans
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle)
WHERE objtype ='Trigger';
GO
```

## <a name="see-also"></a>См. также:
  [Флаги трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с выполнением &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  

