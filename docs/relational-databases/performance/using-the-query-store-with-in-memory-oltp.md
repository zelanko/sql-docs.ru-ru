---
title: Использование хранилища запросов с выполняющейся в памяти OLTP | Документация Майкрософт
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Query Store, in-memory
ms.assetid: aae5ae6d-7c90-4661-a1c5-df704319888a
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: ddb6dcd1078c88237e558d3b7b9ceaabc5f9505a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39554564"
---
# <a name="using-the-query-store-with-in-memory-oltp"></a>Использование хранилища запросов с выполняющейся в памяти OLTP
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Хранилище запросов позволяет отслеживать производительность скомпилированного машинного кода для рабочих нагрузок выполняющейся в памяти OLTP.  
Статистика компиляции и выполнения собирается и отображается так же, как и для рабочих нагрузок на диске.   
При переходе на выполняющуюся в памяти OLTP можно продолжать использовать представления хранилища запросов в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , а также специальные скрипты, разработанные вами для дисковых рабочих нагрузок до миграции. Это позволяет сохранить инвестиции в обучение технологии хранилища запросов, делая ее пригодной для устранения неполадок всех типов рабочих нагрузок.  
Общие сведения об использовании хранилища запросов см. в статье [Monitoring Performance By Using the Query Store](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).  
  
 Использование хранилища запросов с выполняющейся в памяти OLTP не требует какой-либо дополнительной настройки компонентов. Если включить эту функцию в базе данных, она будет работать для всех типов рабочих нагрузок.   
Однако существует ряд определенных аспектов, которые пользователям следует учитывать при использовании хранилища запросов с выполняющейся в памяти OLTP:  
  
-   При включении хранилища запросов по умолчанию собираются запросы, планы и статистика времени компиляции. Тем не менее сбор статистики выполнения не активируется, если только не включить его явно с помощью [sys.sp_xtp_control_query_exec_stats (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md).  
  
-   При установке для *@new_collection_value* значения 0 хранилище запросов прекращает сбор статистики выполнения для соответствующей процедуры или всего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Значение, настроенное с помощью [sys.sp_xtp_control_query_exec_stats (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md), не сохраняется. Не забудьте проверить и заново настроить сбор статистики после перезагрузки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Как и при сборе обычной статистики запросов, при использовании хранилища запросов для отслеживания выполнения рабочих нагрузок может снизиться производительность. Можно рекомендовать включать сбор статистики только для важного подмножества хранимых процедур, скомпилированных в машинный код.  
  
-   Запросы и планы записываются и сохраняются при первой компиляции в машинный код, а затем обновляются при каждой повторной компиляции.  
  
-   Если хранилище запросов включено или его содержимое очищено после компиляции всех хранимых процедур в машинный код, необходимо повторно компилировать их вручную, чтобы они записались в хранилище запросов. Это же правило применяется, если вы удалили запросы вручную с помощью [sp_query_store_remove_query (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md) или [sp_query_store_remove_plan (Transct-SQL)](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md). Для принудительной повторной компиляции процедур используйте [sp_recompile (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-recompile-transact-sql.md).  
  
-   Хранилище запросов использует механизмы создания планов из выполняющейся в памяти OLTP, чтобы записать план выполнения запроса в процессе компиляции. Хранимый план семантически эквивалентен плану, получаемому с использованием `SET SHOWPLAN_XML ON` , но с одним отличием: планы в хранилище запросов разбиваются и хранятся по каждой отдельной инструкции.  
    
-   При запуске хранилища запросов в базе данных со смешанной рабочей нагрузкой можно использовать поле **is_natively_compiled** из [sys.query_store_plan (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md) для быстрого поиска планов запросов, созданных путем компиляции собственного кода.  
  
-   Режим записи хранилища запросов (параметр *QUERY_CAPTURE_MODE* в инструкции **ALTER TABLE**) не влияет на запросы из модулей, скомпилированных в собственном коде, так как они всегда записываются независимо от настроенного значения. Это включает настройку `QUERY_CAPTURE_MODE = NONE`.  
  
-   Продолжительность компиляции запроса, записываемого хранилищем запросов, включает только время, потраченное на оптимизацию запроса перед созданием машинного кода. То есть она не включает время для компиляции кода C и формирования внутренних структур, необходимых для создания кода C.  
  
-   Метрики временно предоставляемых буферов памяти в [sys.query_store_runtime_stats (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md) не заполняются для запросов, скомпилированных в собственном коде. Их значения всегда равны 0. Столбцы временно предоставляемых буферов памяти: avg_query_max_used_memory, last_query_max_used_memory, min_query_max_used_memory, max_query_max_used_memory и stdev_query_max_used_memory.  
  
## <a name="enabling-and-using-query-store-with-in-memory-oltp"></a>Включение и использование хранилища запросов с выполняющейся в памяти OLTP  
 Следующий простой пример демонстрирует использование хранилища запросов с выполняющейся в памяти OLTP в сквозном пользовательском сценарии. В этом примере предполагается, что для базы данных (`MemoryOLTP`) включена выполняющаяся в памяти OLTP.  
    Дополнительные сведения о необходимых компонентах для таблиц, оптимизированных для памяти, см. в разделе [Создание таблиц, оптимизированных для памяти, и хранимых процедур, скомпилированных в собственном коде](../../relational-databases/in-memory-oltp/creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).  
  
```  
USE MemoryOLTP;  
GO  
  
-- Create a simple memory-optimized table   
CREATE TABLE dbo.Ord  
   (OrdNo INTEGER not null PRIMARY KEY NONCLUSTERED,   
    OrdDate DATETIME not null,   
    CustCode NVARCHAR(5) not null)   
WITH (MEMORY_OPTIMIZED=ON);  
GO  
  
-- Enable Query Store before native module compilation  
ALTER DATABASE MemoryOLTP SET QUERY_STORE = ON;  
GO  
  
-- Create natively compiled stored procedure  
CREATE PROCEDURE dbo.OrderInsert(@OrdNo integer, @CustCode nvarchar(5))  
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS   
    BEGIN ATOMIC WITH  
    (TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = N'English')  
  
    DECLARE @OrdDate DATETIME = GETDATE();  
    INSERT INTO dbo.Ord (OrdNo, CustCode, OrdDate)   
        VALUES (@OrdNo, @CustCode, @OrdDate);  
END;  
GO  
  
-- Enable runtime stats collection for queries from dbo.OrderInsert stored procedure  
DECLARE @db_id INT = DB_ID()  
DECLARE @proc_id INT = OBJECT_ID('dbo.OrderInsert');  
DECLARE @collection_enabled BIT;  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1,   
    @database_id = @db_id, @xtp_object_id = @proc_id;  
  
-- Check the state of the collection flag  
EXEC sp_xtp_control_query_exec_stats @database_id = @db_id,   
    @xtp_object_id = @proc_id,   
    @old_collection_value= @collection_enabled output;  
SELECT @collection_enabled AS 'collection status';  
  
-- Execute natively compiled workload  
EXEC dbo.OrderInsert 1, 'A';  
EXEC dbo.OrderInsert 2, 'B';  
EXEC dbo.OrderInsert 3, 'C';  
EXEC dbo.OrderInsert 4, 'D';  
EXEC dbo.OrderInsert 5, 'E';  
  
-- Check Query Store Data  
-- Compile time data  
SELECT q.query_id, plan_id, object_id, query_hash, p.query_plan,  
    p.initial_compile_start_time, p.last_compile_start_time,   
    p.last_execution_time, p.avg_compile_duration,  
    p.last_force_failure_reason, p.force_failure_count  
FROM sys.query_store_query AS q  
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.plan_id  
WHERE q.object_id = OBJECT_ID('dbo.OrderInsert');  
  
-- Get runtime stats  
-- Check count_executions field to verify that runtime statistics   
-- have been collected by the Query Store  
SELECT q.query_id, p.plan_id, object_id, rsi.start_time, rsi.end_time,    
    p.last_force_failure_reason, p.force_failure_count, rs.*  
FROM sys.query_store_query AS q  
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.plan_id  
JOIN sys.query_store_runtime_stats AS rs   
    ON rs.plan_id = p.plan_id  
JOIN sys.query_store_runtime_stats_interval AS rsi   
    ON rs.runtime_stats_interval_id = rsi.runtime_stats_interval_id  
WHERE q.object_id = OBJECT_ID('dbo.OrderInsert');  
```  
  
## <a name="see-also"></a>См. также:  
 [Monitoring Performance By Using the Query Store](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Создание таблиц, оптимизированных для памяти, и хранимых процедур, скомпилированных в собственном коде](../../relational-databases/in-memory-oltp/creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md)   
 [Рекомендации по хранилищу запросов](../../relational-databases/performance/best-practice-with-the-query-store.md)   
 [Хранимые процедуры в хранилище запросов (Transact-SQL)](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [Представления каталога хранилища запросов (Transact-SQL)](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)  
  
  
