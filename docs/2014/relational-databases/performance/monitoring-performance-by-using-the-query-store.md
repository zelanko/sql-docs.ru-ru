---
title: Мониторинг производительности с использованием хранилища запросов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: e06344a4-22a5-4c67-b6c6-a7060deb5de6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bfdce1925bc4c73894e1ff1a9bb0d69f6da94501
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756616"
---
# <a name="monitoring-performance-by-using-the-query-store"></a>Monitoring Performance By Using the Query Store
  Хранилище запросов предоставляет DBA подробные сведения о выборе и производительности плана запросов. Оно упрощает устранение неполадок с производительностью, позволяя быстро находить разницу в производительности, вызванную изменениями в планах запросов. Функция автоматически записывает журнал запросов, планы и статистику выполнения и сохраняет их для просмотра. Она разделяет данные по временным окнам, позволяя просмотреть шаблоны использования и понять, когда изменения плана запросов произошли на сервере. Хранилище запросов можно настроить с помощью параметра [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) .  
  
||  
|-|  
|**Область применения**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([Его](http://azure.micosoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).|  
  
> [!IMPORTANT]  
>  В настоящий момент это предварительная версия функции. Чтобы использовать хранилище запросов, вы должны подтвердить свое согласие с тем, что реализация хранилища запросов соответствует условиям лицензионного соглашения предварительной версии (например, соглашения Enterprise, соглашения для Microsoft Azure или соглашения Microsoft Online Subscription), а также всем применимым [Дополнительным условиям использования для предварительной версии Microsoft Azure](http://azure.microsoft.com/en-us/support/legal/preview-supplemental-terms/).  
  
##  <a name="Enabling"></a> Включение хранилища запросов  
 Хранилище запросов неактивно для новых баз данных по умолчанию.  
  
#### <a name="by-using-the-query-store-page-in-management-studio"></a>На странице «Хранилище запросов» в Management Studio  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши базу данных и выберите **Свойства**. (Требуется версия [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2016 для [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].)  
  
2.  В диалоговом окне **Свойства базы данных** перейдите на страницу **Хранилище запросов** .  
  
3.  В окне **Включение** выберите **True**.  
  
#### <a name="by-using-transact-sql-statements"></a>Используя инструкции Transact-SQL  
  
1.  Используйте инструкцию `ALTER DATABASE`, чтобы включить хранилище запросов. Пример:  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET QUERY_STORE = ON;  
    ```  
  
     Другие параметры синтаксиса, связанные с хранилищем запросов, см. в разделе [Параметры ALTER DATABASE SET (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
> [!NOTE]  
>  Невозможно включить хранилище запросов для базы данных master.  
  

  
##  <a name="About"></a> Сведения о хранилище запросов  
 Планы выполнения для любого специального запроса в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] обычно меняются со временем по разным причинам, например из-за изменения статистики, схемы, создания и удаления индексов и т. д. В кэше процедур (где хранятся кэшированные планы запросов) хранится только последний план выполнения. Планы исключаются из кэша планов из-за нехватки памяти. В результате устранение проблем со снижением производительности запросов, вызванным изменениями планов выполнения, может оказаться сложным и требующим много времени.  
  
 Так как хранилище запросов сохраняет несколько планов выполнения на запрос, оно может принудительно применить политики, чтобы заставить процессор запросов использовать конкретный план выполнения для запроса. Это называется принудительным выполнением плана. Принудительное выполнение плана в хранилище запросов обеспечивается с использованием механизма, аналогичного указанию запроса [USE PLAN](/sql/t-sql/queries/hints-transact-sql-query) , но не требует изменений в приложениях пользователей. Принудительное выполнение плана может решить проблему со снижением производительности запросов, вызванным изменением плана за очень короткий период времени.  
  
 Ниже перечислены стандартные сценарии использования хранилища запросов.  
  
-   Быстрый поиск и устранение снижения производительности планов путем принудительного выполнения предыдущего плана запроса. Исправление запросов, производительность которых была недавно снижена из-за изменений в планах выполнения.  
  
-   Определение количества выполнений запросов за заданный период времени и помощь DBA в устранении неполадок с производительностью ресурсов.  
  
-   Определение первых *n* запросов (по времени выполнения, потреблению памяти и т. д.) за последние *x* часов.  
  
-   Аудит журнала планов запросов для указанного запроса.  
  
-   Анализ шаблонов использования ресурсов (ЦП, операций ввода-вывода и памяти) для определенной базы данных.  
  
 Хранилище запросов содержит два хранилища: **хранилище планов** для сохранения сведений о планах выполнения и **хранилище статистики времени выполнения** для сохранения сведений о статистике выполнения. Количество уникальных планов, которые можно сохранить для запроса в хранилище планов, ограничено параметром конфигурации `max_plans_per_query`. Для повышения производительности сведения записываются в два хранилища асинхронно. Для уменьшения использования свободного места статистические данные времени выполнения в хранилище вычисляются для фиксированного интервала времени. Сведения в этих хранилищах видны при запросе представлений каталога в хранилище запросов.  
  
 Следующий запрос возвращает сведения о запросах и планах в хранилище запросов.  
  
```  
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*  
FROM sys.query_store_plan AS Pl  
JOIN sys.query_store_query AS Qry  
    ON Pl.query_id = Qry.query_id  
JOIN sys.query_store_query_text AS Txt  
    ON Qry.query_text_id = Txt.query_text_id ;  
```  
  

  
## <a name="using-the-regressed-queries-feature"></a>Использование функции сниженных запросов  
 Включив хранилище запросов, обновите информацию о базе данных на панели обозревателя объектов, чтобы добавить раздел **Хранилище запросов** .  
  
 ![Хранилища](../../database-engine/media/querystore.PNG "хранилища")  
  
 При выборе пункта **Сниженные запросы**открывается панель **Сниженные запросы** в [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]. На панели «Сниженные запросы» отображаются запросы и планы в хранилище запросов. В раскрывающихся списках наверху можно выбрать запросы на основе разных условий. Выберите план для просмотра графического плана запросов. С помощью кнопок можно просмотреть исходный запрос, принудительно применить и отменить план запросов, а также обновить отображаемые на экране сведения.  
  
 ![RegressedQueries](../../database-engine/media/regressedqueries.PNG "RegressedQueries")  
  
 Чтобы принудительно выполнить план, выберите запрос и план, а затем щелкните **Принудительно выполнить план** Принудительно выполнять можно только те планы, которые были сохранены с помощью функции плана запросов и все еще хранятся в кэше плана запросов.  
  

  
##  <a name="Options"></a> Параметры конфигурации  
 OPERATION_MODE  
 Может быть равен READ_WRITE или READ_ONLY.  
  
 CLEANUP_POLICY  
 Настройте аргумент STALE_QUERY_THRESHOLD_DAYS, чтобы указать длительность хранения данных в хранилище запросов в днях.  
  
 DATA_FLUSH_INTERVAL_SECONDS  
 Определяет частоту, с которой данные, записанные в хранилище запросов, сохраняются на диск. Для оптимизации производительности данные, собранные хранилищем запросов, асинхронно записываются на диск. Частота, с которой происходит эта асинхронная передача, настраивается с помощью параметра DATA_FLUSH_INTERVAL_SECONDS.  
  
 MAX_SIZE_MB  
 Настраивает максимальный размер хранилища запросов. Если данные в хранилище запросов достигают размера MAX_SIZE_MB, хранилище запроса автоматически изменяет состояние с read-write на read-only и останавливает сбор новых данных.  
  
 INTERVAL_LENGTH_MINUTES  
 Определяет временной интервал вычисления статистических данных о среде выполнения в хранилище запросов. Для оптимизации использования свободного места статистические данные времени выполнения в хранилище вычисляются для фиксированного интервала времени. Этот интервал настраивается с помощью параметра INTERVAL_LENGTH_MINUTES.  
  
 Запросите представление `sys.database_query_store_options`, чтобы определить текущие параметры хранилища запросов.  
  
 Дополнительные сведения о настройке параметров с помощью инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в разделе [Управление параметрами](#OptionMgmt).  
  
 
  
##  <a name="Related"></a> Связанные представления, функции и процедуры  
 Хранилище запросов можно просмотреть и контролировать в [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] либо с помощью следующих представлений и процедур.  
  
-   [sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql)  
  
### <a name="query-store-catalog-views"></a>Представления каталога хранилища запросов  
 В семи представлениях каталога представлены сведения о хранилище запросов.  
  
-   [sys.database_query_store_options (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql)  
  
-   [sys.query_context_settings (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-query-context-settings-transact-sql)  
  
-   [sys.query_store_plan (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-query-store-plan-transact-sql)  
  
-   [sys.query_store_query (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-query-store-query-transact-sql)  
  
-   [sys.query_store_query_text (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql)  
  
-   [sys.query_store_runtime_stats (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql)  
  
-   [sys.query_store_runtime_stats_interval (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql)  
  
### <a name="query-store-stored-procedures"></a>Хранимые процедуры в хранилище запросов,  
 Шесть хранимых процедур настраивают хранилище запросов.  
  
-   [sp_query_store_flush_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql)  
  
-   [sp_query_store_reset_exec_stats (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql)  
  
-   [sp_query_store_force_plan (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql)  
  
-   [sp_query_store_unforce_plan (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql)  
  
-   [sp_query_store_remove_plan (Transct-SQL)](/sql/relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql)  
  
-   [sp_query_store_remove_query (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql)  
  

  
##  <a name="Scenarios"></a> Основные сценарии использования  
  
###  <a name="OptionMgmt"></a> Управление параметрами  
 В этом разделе представлены некоторые рекомендации по управлению самой функцией хранилища запросов.  
  
 **Активно ли сейчас хранилище запросов?**  
  
 Данные в хранилище запросов содержатся в базе данных пользователя, поэтому их размер ограничен (настраивается с помощью `MAX_STORAGE_SIZE_MB`). Если размер данных в хранилище запросов достигнет предела, хранилище запросов автоматически изменит состояние с read-write на read-only и перестанет собирать новые данные.  
  
 Выполните следующий сценарий, чтобы определить, активно ли хранилище запросов и собирает ли оно статистику времени выполнения.  
  
```  
DECLARE @x nvarchar(100) = CAST(newid() AS nvarchar(100));  
DECLARE @query nvarchar(max) =   
N'IF EXISTS  
(  
    SELECT *   
    FROM sys.query_store_query_text   
    WHERE query_sql_text LIKE ''%' + @x + N'%''  
)  
SELECT ''Query Store is active'' ;  
ELSE SELECT ''Query Store is NOT active''' ;  
EXEC sp_executesql @query;  
```  
  
 **Получение параметров запросов**  
  
 Чтобы найти подробные сведения о состоянии хранилища запросов, выполните следующую команду в базе данных пользователя.  
  
```  
SELECT * FROM sys.database_query_store_options;  
```  
  
 **Задание интервала для хранилища запросов**  
  
 Вы можете переопределить интервал для объединения статистики времени выполнения запросов (по умолчанию — 60 минут).  
  
```  
  
      USE master;  
GO  
  
ALTER DATABASE <database_name>   
SET QUERY_STORE (INTERVAL_LENGTH_MINUTES = 15);  
```  
  
 Обратите внимание, что произвольные значения не допускаются. следует использовать один из следующих: 1, 5, 10, 15, 30 и 60.  
  
 Новое значение интервала находится в представлении `sys.database_query_store_options`.  
  
 Если хранилище запросов заполнено, используйте следующую инструкцию для его расширения.  
  
```  
ALTER DATABASE <database_name>   
SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <new_size>);  
```  
  
 **Задание всех параметров для хранилища запросов**  
  
 Вы можете задать несколько параметров хранилища запросов одновременно с помощью одной инструкции ALTER DATABASE.  
  
```  
ALTER DATABASE <database name>   
SET QUERY_STORE (  
    OPERATION_MODE = READ_WRITE,  
    CLEANUP_POLICY =   
    (STALE_QUERY_THRESHOLD_DAYS = 30),  
    DATA_FLUSH_INTERVAL_SECONDS = 3000,  
    MAX_STORAGE_SIZE_MB = 500,  
    INTERVAL_LENGTH_MINUTES = 15  
);  
```  
  
 **Очистка пространства**  
  
 Внутренние таблицы хранилища запросов создаются в группе файлов PRIMARY во время создания базы данных, и эту конфигурацию невозможно изменить позже. Если у вас заканчивается место, следует удалить более старые данные из хранилища запросов с помощью следующей инструкции.  
  
```  
ALTER DATABASE <db_name> SET QUERY_STORE CLEAR;  
```  
  
 Кроме того, можно очистить только данные ad-hoc-запросов, так как они менее актуальны для оптимизации запросов и анализа планов, но занимают столько же места.  
  
 **Удаление ad-hoc-запросов** . Эта функция удаляет запросы, которые были выполнены только один раз более 24 часов назад.  
  
```  
DECLARE @id int  
DECLARE adhoc_queries_cursor CURSOR   
FOR   
SELECT q.query_id  
FROM sys.query_store_query_text AS qt  
JOIN sys.query_store_query AS q   
    ON q.query_text_id = qt.query_text_id  
JOIN sys.query_store_plan AS p   
    ON p.query_id = q.query_id  
JOIN sys.query_store_runtime_stats AS rs   
    ON rs.plan_id = p.plan_id  
GROUP BY q.query_id  
HAVING SUM(rs.count_executions) < 2   
AND MAX(rs.last_execution_time) < DATEADD (hour, -24, GETUTCDATE())  
ORDER BY q.query_id ;  
  
OPEN adhoc_queries_cursor ;  
FETCH NEXT FROM adhoc_queries_cursor INTO @id;  
WHILE @@fetch_status = 0  
    BEGIN   
        PRINT @id  
        EXEC sp_query_store_remove_query @id  
        FETCH NEXT FROM adhoc_queries_cursor INTO @id  
    END   
CLOSE adhoc_queries_cursor ;  
DEALLOCATE adhoc_queries_cursor;  
```  
  
 Вы можете задать собственную процедуру с другой логикой для очистки данных, которые вам больше не требуются.  
  
 В примере выше используется расширенная хранимая процедура `sp_query_store_remove_query` для удаления ненужных данных. Вы можете также использовать две другие процедуры.  
  
-   `sp_query_store_reset_exec_stats` — Удаление статистики времени выполнения для указанного плана.  
  
-   `sp_query_store_remove_plan` — Удаление одного плана.  
  

  
###  <a name="Peformance"></a> Аудит производительности и устранение проблем  
 Так как в хранилище запросов ведется журнал метрик компиляции и времени выполнения при выполнении запросов, возникает множество разных вопросов в отношении рабочей нагрузки, на которые вы легко можете ответить.  
  
 **Последний *n* запросы, выполняемые в базе данных.**  
  
```  
SELECT TOP 10 qt.query_sql_text, q.query_id,   
    qt.query_text_id, p.plan_id, rs.last_execution_time  
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.query_id   
JOIN sys.query_store_runtime_stats AS rs   
    ON p.plan_id = rs.plan_id  
ORDER BY rs.last_execution_time DESC;  
```  
  
 **Число выполнений для каждого запроса.**  
  
```  
SELECT q.query_id, qt.query_text_id, qt.query_sql_text,   
    SUM(rs.count_executions) AS total_execution_count  
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.query_id   
JOIN sys.query_store_runtime_stats AS rs   
    ON p.plan_id = rs.plan_id  
GROUP BY q.query_id, qt.query_text_id, qt.query_sql_text  
ORDER BY total_execution_count DESC;  
```  
  
 **Число запросов с наибольшим средним временем выполнения за последний час.**  
  
```  
SELECT TOP 10 rs.avg_duration, qt.query_sql_text, q.query_id,  
    qt.query_text_id, p.plan_id, GETUTCDATE() AS CurrentUTCTime,   
    rs.last_execution_time   
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.query_id   
JOIN sys.query_store_runtime_stats AS rs   
    ON p.plan_id = rs.plan_id  
WHERE rs.last_execution_time > DATEADD(hour, -1, GETUTCDATE())  
ORDER BY rs.avg_duration DESC;  
```  
  
 **Число запросов, в которых возникли крупнейших среднее физических операций ввода-ВЫВОДА считывает за последние 24 часа, с указанием среднего количества строк и выполнений.**  
  
```  
SELECT TOP 10 rs.avg_physical_io_reads, qt.query_sql_text,   
    q.query_id, qt.query_text_id, p.plan_id, rs.runtime_stats_id,   
    rsi.start_time, rsi.end_time, rs.avg_rowcount, rs.count_executions  
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p   
    ON q.query_id = p.query_id   
JOIN sys.query_store_runtime_stats AS rs   
    ON p.plan_id = rs.plan_id   
JOIN sys.query_store_runtime_stats_interval AS rsi   
    ON rsi.runtime_stats_interval_id = rs.runtime_stats_interval_id  
WHERE rsi.start_time >= DATEADD(hour, -24, GETUTCDATE())   
ORDER BY rs.avg_physical_io_reads DESC;  
```  
  
 **Запросы с несколькими планами.** Эти запросы особенно интересны, так как они являются кандидатами на снижение из-за изменения выбранного плана. Следующий запрос определяет данные запросы со всеми планами.  
  
```  
WITH Query_MultPlans  
AS  
(  
    SELECT COUNT(*) AS cnt, q.query_id   
    FROM sys.query_store_query_text AS qt  
    JOIN sys.query_store_query AS q  
        ON qt.query_text_id = q.query_text_id  
    JOIN sys.query_store_plan AS p  
        ON p.query_id = q.query_id  
    GROUP BY q.query_id  
    HAVING COUNT(distinct plan_id) > 1  
)  
  
SELECT q.query_id, object_name(object_id) AS ContainingObject, query_sql_text,  
plan_id, p.query_plan AS plan_xml,  
p.last_compile_start_time, p.last_execution_time  
FROM Query_MultPlans AS qm  
JOIN sys.query_store_query AS q  
    ON qm.query_id = q.query_id  
JOIN sys.query_store_plan AS p  
    ON q.query_id = p.query_id  
JOIN sys.query_store_query_text qt   
    ON qt.query_text_id = q.query_text_id  
ORDER BY query_id, plan_id;  
```  
  
 **Запросов недавно понизилась производительность (по сравнению с другой точкой во времени).** Следующий пример запроса возвращает все запросы, для которых время выполнения удвоилось за последние 48 часов из-за изменения выбранного плана. Запрос сравнивает все интервалы статистики времени выполнения.  
  
```  
SELECT   
    qt.query_sql_text,   
    q.query_id,   
    qt.query_text_id,   
    rs1.runtime_stats_id AS runtime_stats_id_1,  
    rsi1.start_time AS interval_1,   
    p1.plan_id AS plan_1,   
    rs1.avg_duration AS avg_duration_1,   
    rs2.avg_duration AS avg_duration_2,  
    p2.plan_id AS plan_2,   
    rsi2.start_time AS interval_2,   
    rs2.runtime_stats_id AS runtime_stats_id_2  
FROM sys.query_store_query_text AS qt   
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_text_id   
JOIN sys.query_store_plan AS p1   
    ON q.query_id = p1.query_id   
JOIN sys.query_store_runtime_stats AS rs1   
    ON p1.plan_id = rs1.plan_id   
JOIN sys.query_store_runtime_stats_interval AS rsi1   
    ON rsi1.runtime_stats_interval_id = rs1.runtime_stats_interval_id   
JOIN sys.query_store_plan AS p2   
    ON q.query_id = p2.query_id   
JOIN sys.query_store_runtime_stats AS rs2   
    ON p2.plan_id = rs2.plan_id   
JOIN sys.query_store_runtime_stats_interval AS rsi2   
    ON rsi2.runtime_stats_interval_id = rs2.runtime_stats_interval_id  
WHERE rsi1.start_time > DATEADD(hour, -48, GETUTCDATE())   
    AND rsi2.start_time > rsi1.start_time   
    AND p1.plan_id <> p2.plan_id  
    AND rs2.avg_duration > 2*rs1.avg_duration  
ORDER BY q.query_id, rsi1.start_time, rsi2.start_time;  
```  
  
 Если вы хотите просмотреть производительность всех регрессий (а не только тех, которые связаны с изменением выбранного плана), удалите условие `AND p1.plan_id <> p2.plan_id` из предыдущего запроса.  
  
 **Запросы, которые недавно понизилась производительность (сравнение последней и журнал выполнения).** Следующий запрос сравнивает периоды выполнения на основе выполнения запросов. В этом примере запрос сравнивает выполнение за последний период (1 час) с периодом журнала (последний день) и определяет те, которые были представлены в additional_duration_workload. Эти метрики подсчитываются путем умножения разницы между средним последним выполнением и средним выполнением по журналу на количество последних выполнений. Фактически они представляют количество последних выполнений с дополнительной длительностью по сравнению с журналом:  
  
```  
--- "Recent" workload - last 1 hour  
DECLARE @recent_start_time datetimeoffset;  
DECLARE @recent_end_time datetimeoffset;  
SET @recent_start_time = DATEADD(hour, -1, SYSUTCDATETIME());  
SET @recent_end_time = SYSUTCDATETIME();  
  
--- "History" workload  
DECLARE @history_start_time datetimeoffset;  
DECLARE @history_end_time datetimeoffset;  
SET @history_start_time = DATEADD(hour, -24, SYSUTCDATETIME());  
SET @history_end_time = SYSUTCDATETIME();  
  
WITH  
hist AS  
(  
    SELECT   
        p.query_id query_id,   
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration,   
        SUM(rs.count_executions) count_executions,  
        COUNT(distinct p.plan_id) num_plans   
     FROM sys.query_store_runtime_stats AS rs  
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id  
    WHERE  (rs.first_execution_time >= @history_start_time AND rs.last_execution_time < @history_end_time)  
        OR (rs.first_execution_time <= @history_start_time AND rs.last_execution_time > @history_start_time)  
        OR (rs.first_execution_time <= @history_end_time AND rs.last_execution_time > @history_end_time)  
    GROUP BY p.query_id  
),  
recent AS  
(  
    SELECT   
        p.query_id query_id,   
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration,   
        SUM(rs.count_executions) count_executions,  
        COUNT(distinct p.plan_id) num_plans   
    FROM sys.query_store_runtime_stats AS rs  
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id  
    WHERE  (rs.first_execution_time >= @recent_start_time AND rs.last_execution_time < @recent_end_time)  
        OR (rs.first_execution_time <= @recent_start_time AND rs.last_execution_time > @recent_start_time)  
        OR (rs.first_execution_time <= @recent_end_time AND rs.last_execution_time > @recent_end_time)  
    GROUP BY p.query_id  
)  
SELECT   
    results.query_id query_id,  
    results.query_text query_text,  
    results.additional_duration_workload additional_duration_workload,  
    results.total_duration_recent total_duration_recent,  
    results.total_duration_hist total_duration_hist,  
    ISNULL(results.count_executions_recent, 0) count_executions_recent,  
    ISNULL(results.count_executions_hist, 0) count_executions_hist   
FROM  
(  
    SELECT  
        hist.query_id query_id,  
        qt.query_sql_text query_text,  
        ROUND(CONVERT(float, recent.total_duration/recent.count_executions-hist.total_duration/hist.count_executions)*(recent.count_executions), 2) AS additional_duration_workload,  
        ROUND(recent.total_duration, 2) total_duration_recent,   
        ROUND(hist.total_duration, 2) total_duration_hist,  
        recent.count_executions count_executions_recent,  
        hist.count_executions count_executions_hist     
    FROM hist   
        JOIN recent   
            ON hist.query_id = recent.query_id   
        JOIN sys.query_store_query AS q   
            ON q.query_id = hist.query_id  
        JOIN sys.query_store_query_text AS qt   
            ON q.query_text_id = qt.query_text_id      
) AS results  
WHERE additional_duration_workload > 0  
ORDER BY additional_duration_workload DESC  
OPTION (MERGE JOIN);  
```  
  

  
###  <a name="Stability"></a> Обеспечение стабильной производительности запросов  
 Вы могли заметить, что для запросов, которые выполняются несколько раз, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовал разные планы, что привело к другому уровню нагрузки и длительности использования ресурсов. В хранилище запросов вы можете легко обнаружить снижение производительности и определить оптимальный план за интересующий вас период. Затем вы можете принудительно применить оптимальный план для выполнения будущих запросов.  
  
 Вы можете также определить несоответствующую производительность запросов для запроса с параметрами (заданными автоматически или вручную). Среди разных планов вы можете найти достаточно быстрый и оптимальный план для всех или большинства значений параметров и принудительно применить его, сохранив прогнозируемую производительность для более широкого набора сценариев пользователя.  
  
 **Планирование или принудительное выполнение запроса (применение политики принудительного выполнения).** При принудительном применении определенного плана каждый раз, когда запрос выполняется, он будет выполняться в принудительно выбранном плане.  
  
```  
EXEC sp_query_store_force_plan @query_id = 48, @plan_id = 49;  
```  
  
 При использовании `sp_query_store_force_plan` можно принудительно выполнять только планы, записанные хранилищем запросов в качестве плана для этого запроса. Другими словами, единственные доступные планы — это те, которые уже использовались для выполнения Q1, когда хранилище запросов было активно.  
  
 **Удаление принудительного применения плана для запроса.** Чтобы снова использовать оптимизатор запросов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для вычисления оптимального плана запросов, используйте `sp_query_store_unforce_plan` для отмены принудительного выполнения плана, выбранного для запроса.  
  
```  
EXEC sp_query_store_unforce_plan @query_id = 48, @plan_id = 49;  
```  
  

  
## <a name="see-also"></a>См. также  
 [Monitor and Tune for Performance](../performance/monitor-and-tune-for-performance.md)   
 [Средства контроля и настройки производительности](../performance/performance-monitoring-and-tuning-tools.md)   
 [Открытие монитора активности (среда SQL Server Management Studio)](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)   
 [Монитор активности](../performance-monitor/activity-monitor.md)  
  
  
