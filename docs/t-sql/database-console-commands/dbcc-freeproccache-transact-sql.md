---
title: "Инструкция DBCC FREEPROCCACHE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FREEPROCCACHE_TSQL
- FREEPROCCACHE
- DBCC_FREEPROCCACHE_TSQL
- DBCC FREEPROCCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- freeing procedure cache
- removing procedure cache elements
- deleting procedure cache elements
- DBCC FREEPROCCACHE statement
- procedure cache [SQL Server]
- clearing procedure cache
ms.assetid: 0e09d210-6f23-4129-aedb-3d56b2980683
caps.latest.revision: 61
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bda4cf8c1859d011e0a320887fd8a9cc53d8cea0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-freeproccache-transact-sql"></a>DBCC FREEPROCCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

Удаляет все элементы из кэша планов, удаляет заданный план из кэша планов с помощью указания дескриптора плана или дескриптора SQL либо удаляет все записи кэша, связанные с указанным пулом ресурсов.

>[!NOTE]
>DBCC FREEPROCCACHE не очищает статистику выполнения для хранимых процедур, скомпилированных в собственном коде. Кэш процедур не содержит сведения о хранимых процедурах, скомпилированных в собственном коде. Все статистические данные выполнения, собранные при выполнении процедуры будут отображаться в статистику выполнения динамических административных представлений: [sys.dm_exec_procedure_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md) и [sys.dm_exec_query_plan &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md).  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
Синтаксис для SQL Server:

```sql
DBCC FREEPROCCACHE [ ( { plan_handle | sql_handle | pool_name } ) ] [ WITH NO_INFOMSGS ]  
```  

Синтаксис для хранилища данных Azure SQL и параллельные хранилища данных:
  
```sql
DBCC FREEPROCCACHE [ ( COMPUTE | ALL ) ] 
     [ WITH NO_INFOMSGS ]   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 ({ *plan_handle* | *sql_handle* | *pool_name* })  
 *plan_handle* уникальным образом определяет план запроса для пакета, который был выполнен и план которого хранится в кэше планов. *plan_handle* — **varbinary(64)** и может быть получен из следующих объектов DMO:  
 -   [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
 -   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
 -   [sys.dm_exec_query_memory_grants](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  
 -   [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  

 *sql_handle* дескриптор SQL очищаемого пакета. *sql_handle* — **varbinary(64)** и может быть получен из следующих объектов DMO:  
 -   [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
 -   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
 -   [sys.dm_exec_cursors](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cursors-transact-sql.md)  
 -   [sys.dm_exec_xml_handles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)  
 -   [sys.dm_exec_query_memory_grants](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  

 *pool_name* имя пула ресурсов регулятора ресурсов. *pool_name* — **sysname** и может быть получен с помощью запроса к [sys.dm_resource_governor_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md) динамическое административное представление.  
 Чтобы связать группу рабочей нагрузки регулятора ресурсов с пулом ресурсов, запросите [sys.dm_resource_governor_workload_groups](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md) динамическое административное представление. Сведения о группе рабочей нагрузки для сеанса, запросите [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md) динамическое административное представление.  

  
 WITH NO_INFOMSGS  
 Подавляет вывод всех информационных сообщений.  
  
 COMPUTE  
 Очистка кэша планов запросов из каждого вычислительного узла. Это значение по умолчанию.  
  
 ALL  
 Очистка кэша планов запросов из каждый вычислительный узел и узел элемента управления.  
  
## <a name="remarks"></a>Замечания  
Инструкция DBCC FREEPROCCACHE используется для аккуратной очистки кэша планов. Освобождение кэша планов приводит, например, к тому, что хранимая процедура повторно компилируется, а не используется из кэша. 

Это может стать причиной внезапного временного снижения производительности обработки запросов. Для каждого очищенного хранилища кэша в кэше планов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнал ошибок содержит следующее информационное сообщение: «[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил %d экземпляров, сброшенных на диск хранилищ кэша для хранилища кэша «%s» (части кэша планов) из-за "DBCC FREEPROCCACHE' или 'DBCC FREESYSTEMCACHE' операции.» Это сообщение добавляется в журнал каждые пять минут при сбросе кэша в течение этого интервала времени.

Следующие операции по перенастройке также очищают кэш процедур:  
-   доступ к счетчику контейнеров проверки кэша  
-   доступ к квоте кэша проверки  
-   clr enabled  
-   стоимостный порог для параллелизма  
-   cross db ownership chaining  
-   память для создания индекса  
-   максимальная степень параллелизма  
-   max server memory  
-   max text repl size  
-   максимальное количество рабочих потоков  
-   min memory per query  
-   min server memory  
-   ограничение стоимости регулятора запросов  
-   ожидание запроса  
-   remote query timeout  
-   user options  
  
## <a name="result-sets"></a>Результирующие наборы  
Если предложение WITH NO_INFOMSGS не указано, инструкция DBCC FREEPROCCACHE возвращает: «выполнение инструкции DBCC завершено. Если инструкция DBCC выдает сообщения об ошибках, обратитесь к системному администратору».
  
## <a name="permissions"></a>Permissions  
Применяется к: SQL Server, параллельные хранилища данных 

- Требует разрешения ALTER SERVER STATE на сервере.  

Область применения этой статьи: Хранилище данных SQL Azure
- Требуется членство в фиксированной серверной роли DB_OWNER.  

## <a name="general-remarks-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Общие замечания для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Одновременно может выполняться несколько команд DBCC FREEPROCCACHE.
В [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], очистка кэша планов запроса может вызвать временное снижение производительности запросов при перекомпиляции запросов. 

DBCC FREEPROCCACHE (вычислительные ресурсы) только вызывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на перекомпиляцию запросов, когда они запускаются на вычислительных узлах. Это не вызывает [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] необходимость в повторной компиляции плана параллельного запроса, создаваемого на узел элемента управления.
Инструкция DBCC FREEPROCCACHE может быть отменено во время выполнения.
  
## <a name="limitations-and-restrictions-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ограничения для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Инструкция DBCC FREEPROCCACHE не может выполняться в транзакции.
DBCC FREEPROCCAHCE не поддерживается в инструкции ОПИСАНИЯ.
  
## <a name="metadata-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Метаданные для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Новая строка добавляется в системном представлении sys.pdw_exec_requests при выполнении инструкции DBCC FREEPROCCACHE.
  
## <a name="examples-includessnoversionincludesssnoversion-mdmd"></a>Примеры:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
### <a name="a-clearing-a-query-plan-from-the-plan-cache"></a>A. Очистка плана запроса из кэша планов  
В следующем примере план запроса очищается из кэша планов путем указания дескриптора плана запроса. Чтобы обеспечить наличие запроса-образца в кэше планов, сначала выполните следующий запрос. `sys.dm`_`exec` \_ `cached_plans` И `sys.dm` \_ `exec` \_ `sql` \_ `text` динамические административные представления запрашиваются для возврата дескриптор плана для запроса. 

Затем значение дескриптора плана из результирующего набора вставляется в инструкцию `DBCC FREEPROCACHE` для удаления из кэша планов именно этого плана.
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT * FROM Person.Address;  
GO  
SELECT plan_handle, st.text  
FROM sys.dm_exec_cached_plans   
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st  
WHERE text LIKE N'SELECT * FROM Person.Address%';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

{!!! Текст Mispalced? !!!}
 `plan_handle                                         text`  
  
 `--------------------------------------------------  -----------------------------`  
  
 `0x060006001ECA270EC0215D05000000000000000000000000  SELECT * FROM Person.Address;`  
  
 `(1 row(s) affected)`  
{текст misplaed окончания попросите}
  
```sql  
-- Remove the specific plan from the cache.  
DBCC FREEPROCCACHE (0x060006001ECA270EC0215D05000000000000000000000000);  
GO  
```  
  
### <a name="b-clearing-all-plans-from-the-plan-cache"></a>Б. Очистка всех планов из кэша планов  
В следующем примере из кэша планов удаляются все элементы. WITH `NO_INFOMSGS` указано предложение, чтобы избежать отображения информационного сообщения.
  
```sql  
DBCC FREEPROCCACHE WITH NO_INFOMSGS;  
```  
  
### <a name="c-clearing-all-cache-entries-associated-with-a-resource-pool"></a>В. Очистка всех записей кэша, связанных с пулом ресурсов  
В следующем примере очищаются все записи кэша, связанные с указанным пулом ресурсов. `sys.dm_resource_governor_resource_pools` Сначала запрашивается представление для получения значения для *pool_name*.
  
```sql  
SELECT * FROM sys.dm_resource_governor_resource_pools;  
GO  
DBCC FREEPROCCACHE ('default');  
GO  
```  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-dbcc-freeproccache-basic-syntax-examples"></a>Г. Примеры базовый синтаксис инструкции DBCC FREEPROCCACHE  
В следующем примере удаляется всех кэшей существующий план запроса от вычислительных узлов. Несмотря на то, что контекст имеет значение UserDbSales, кэши вычислений запрос узла плана для всех баз данных будет будут удалены. Предложение WITH NO_INFOMSGS запрещает информационные сообщения в результатах.  
  
```sql
USE UserDbSales;  
DBCC FREEPROCCACHE (COMPUTE) WITH NO_INFOMSGS;  
```  
  
 Следующий пример содержит те же результаты, что и предыдущий пример, за исключением того, информационные сообщения будут отображаться в результатах.  
  
```sql
USE UserDbSales;  
DBCC FREEPROCCACHE (COMPUTE);  
```  
  
Запрашиваются информационных сообщений и выполнения проходит успешно, результаты запроса после одной строке на вычислительном узле.
  
### <a name="e-granting-permission-to-run-dbcc-freeproccache"></a>Д. Предоставление разрешения на запуск инструкции DBCC FREEPROCCACHE  
Следующий пример предоставляет Дэвид разрешение для запуска DBCC FREEPROCCACHE.  
  
```sql
GRANT ALTER SERVER STATE TO David;  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)
  
  

