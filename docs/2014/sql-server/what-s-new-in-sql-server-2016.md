---
title: Новые возможности SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 12/10/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- new features [SQL Server]
- SQL Server, what's new
- SQL Server 2008 what's new
- what's new [SQL Server]
- sql server 2014 sp1
- sql server 2014 sp2
ms.assetid: 6a428023-e3cc-4626-a88a-4c13ccbd7db0
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 23a1392256e103fa1bc112f11b5c5b97f5c398f1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "75237705"
---
# <a name="whats-new-in-sql-server-2014"></a>Новые возможности SQL Server 2014

В этом разделе приведены подробные ссылки на новые функции в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] и сводные данные о пакетах служб для[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**Попробуйте.** ![виртуальная машина Azure Small](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png) имеет учетную запись Azure?  Перейдите в https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2 раздел, чтобы запустить виртуальную машину с уже установленным SQL Server 2014 с пакетом обновления 1 (SP1).

> [!TIP]
> [Щелкните здесь](../2014-toc/index.yml) , чтобы получить домашнюю страницу документации SQL Server 2014.

<!--
Do not let this file's filename fool you.
This filename contains "2016", but nevertheless...
This file, at this exact GitHub path, is dedicated to SQL Server version 2014.
-->

## <a name="whats-new-articles"></a>Статьи о новых возможностях

-   [Новые возможности &#40;ядро СУБД&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [Новые возможности служб Analysis Services и бизнес-аналитики](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)  
  
-   [Новые возможности установки SQL Server](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]не предоставила существенных новых возможностей для следующих компонентов:**  
  
-   [Новые возможности &#40;Integration Services&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [Новые возможности &#40;Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="sssql14-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] с пакетом обновления 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)](С пакетом обновления 1 (SP1)) не вносит существенные новые функции.
-  [SQL Server 2014. сведения о выпуске пакета обновления 1 (SP1)](https://support.microsoft.com/kb/3058865).
-  [Загрузите пакет обновления 1 (SP1) для Microsoft SQL Server 2014, скачайте пакет обновления 1 (SP1) для Microsoft SQL Server 2014. ![](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/download/details.aspx?id=46694) [Download Service Pack 1 for Microsoft SQL Server 2014](https://www.microsoft.com/download/details.aspx?id=46694)


## <a name="sssql14-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]Пакет обновления 2 (SP2)
- [Сведения о выпуске пакета обновления 2 для SQL Server 2014](https://support.microsoft.com/kb/3171021).
-  [Загрузите пакет обновления 2 (SP2) для Microsoft SQL Server 2014, скачайте пакет обновления 2 (SP2) для Microsoft SQL Server 2014. ![](./media/what-s-new-in-sql-server-2016/download.png)](https://go.microsoft.com/fwlink/?LinkID=821558) [Download Service Pack 2 for Microsoft SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=821558)
-  Загрузите пакет дополнительных компонентов [SQL Server 2014 с пакетом обновления 2 (SP2) для SQL Server 2014. ![](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/download/details.aspx?id=53164) [Download the SQL Server 2014 SP2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=53164)

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]SP2 Включает следующие усовершенствования.

### <a name="performance-and-scalability-improvements"></a>Улучшения производительности и масштабируемости 
-   **Автоматическое секционирование с мягкими NUMA:** В [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] с пакетом обновления 2 (SP2) автоматическое мягкое NUMA включено при включении флага трассировки 8079 во время запуска экземпляра. Когда флаг трассировки 8079 включен во время запуска, [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] пакет обновления 2 (SP2) выполнит опрос структуры оборудования и автоматически настроит Soft NUMA в системах, сообщающих 8 или больше процессоров на узел NUMA. Автоматическое, мягкое поведение NUMA поддерживает технологию Hyper-Threading (HT/логический процессор). Секционирование и создание дополнительных узлов позволяет масштабировать фоновую обработку за счет увеличения числа прослушивателей и масштаба вычислений, а также расширения возможностей сети и шифрования. Рекомендуется сначала протестировать рабочую нагрузку с использованием автоматического программного NUMA, прежде чем настраивать его в рабочей среде. Дополнительные [сведения см. в блоге](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/). 
-  **Динамическая память масштабирование объектов:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] пакет обновления 2 (SP2) динамически разделяет объекты памяти на основе числа узлов и ядер для масштабирования на современном оборудовании. Цель динамического продвижения — автоматическое секционирование объекта КМЕМСРЕАДной памяти в потоковой безопасности, если это становится узким местом. Несекционированные объекты памяти можно динамически секционировать по узлу (количество секций равно количеству узлов NUMA). Объекты памяти, разделенные узлом, могут дополнительно секционированы по ЦП (количество секций равно количеству ЦП). Дополнительные [сведения см. в блоге](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/).
-  **Указание MAXDOP для команд DBCC\* Check:** это улучшение устраняет [отзывы о подключении (468694)](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb). Теперь можно выполнить инструкцию DBCC CHECKDB с параметром MAXDOP, отличным от значения sp_configure. Если MAXDOP превышает значение, настроенное с помощью Resource Governor, ядро СУБД использует значение MAXDOP из Resource Governor, как описано в статье "ALTER WORKLOAD GROUP (Transact-SQL)". Все семантические правила, используемые параметром конфигурации max degree of parallelism, применимы при использовании указания запроса MAXDOP. Дополнительные сведения см. в разделе [DBCC CHECKDB (Transact-SQL)](https://msdn.microsoft.com/library/ms176064.aspx).
-   **Включите >8 ТБ для буферного пула:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] с пакетом обновления 2 (SP2) обеспечивает 128 ТБ виртуального адресного пространства для использования буферного пула. Это улучшение позволяет SQL Server буферный пул масштабироваться свыше 8 ТБ на современном оборудовании.
-   **SOS_RWLockное улучшение блокировки:** SOS_RWLock — это примитив синхронизации, используемый в различных местах во всей SQL Server базе кода.  Как следует из названия, код может иметь несколько общих (читающих) или единичных (Writer) владельцев. Это улучшение устраняет необходимость в взаимоблокировке для SOS_RWLock и вместо этого использует методы без блокировки, аналогичные функциям OLTP в памяти. Благодаря этому изменению многие потоки могут считывать структуру данных, защищенную SOS_RWLock параллельно, не блокируя друг друга. Такая параллелизации обеспечивает повышенную масштабируемость. До этого изменения реализация спин-блокировки позволяла только одному потоку получать SOS_RWLock за раз, даже считывать структуру данных. Дополнительные [сведения см. в блоге](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/).
-    **Реализация пространственных машин:** Значительное улучшение производительности пространственных запросов представлено в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] пакете обновления 2 (SP2) с помощью собственной реализации. Дополнительные сведения см. в [статье базы знаний KB3107399](https://support.microsoft.com/kb/3107399).

### <a name="supportability-and-diagnostics-improvements"></a>Улучшения поддержки и диагностики
-   **Клонирование базы данных:** Клонирование базы данных — это новая команда DBCC, которая улучшает устранение неполадок в существующих рабочих базах данных путем клонирования схемы и метаданных без данных. Клон создается с помощью команды `DBCC clonedatabase('source_database_name', 'clone_database_name')`.  **Примечание.** Клонированные базы данных не следует использовать в рабочих средах. Используйте следующую команду, чтобы определить, была ли создана база данных из клонированной базы данных `select DATABASEPROPERTYEX('clonedb', 'isClone')`:. Возвращаемое значение **1** указывает, что база данных создается из clonedatabase, а **0** означает, что она не является клоном.
-   **Поддержка tempdb:**  Новое сообщение журнала ошибок, которое указывает на запуск как количества файлов tempdb, так и размера и автоувеличения файлов данных tempdb.
-   **Ведение журнала инициализации мгновенных файлов базы данных:** Новое сообщение журнала ошибок, которое указывает на запуск сервера, состояние немедленной инициализации файлов базы данных (включено или отключено).
-   **Имена модулей в стеке вызовов:** Стек вызовов расширенных событий (XEvent) теперь включает имена модулей и смещение, а не абсолютные адреса.
-   **Новые DMF для добавочной статистики:** Это улучшение устраняет [обратную связь Connect (797156)](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics) , чтобы включить отслеживание добавочной статистики на уровне секции. Появилась новая DMF sys. dm_db_incremental_stats_properties для предоставления сведений по разделам для добавочной статистики.
-   **Обновление поведения динамического административного представления использования индекса:** Это улучшение устраняет [обратную связь (739566)](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats) от клиентов, где перестроение индекса *не* приведет к очистке существующей записи строки из sys. dm_db_index_usage_stats для этого индекса. Теперь поведение будет таким же, как в SQL 2008 и SQL Server 2016. Дополнительные [сведения см. в блоге](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/).
-   **Улучшенная корреляция между диагностическими данными XE и DMV:** Это улучшение устраняет [Отзывы о подключении (1934583)](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types). `Query_hash`и `query_plan_hash` используются для уникальной идентификации запроса. Динамическое административное представление определяет их как varbinary(8), а XEvent определяет их как UINT64. Поскольку SQL Server не имеет неподписанного типа bigint, приведение не всегда работает. В этом усовершенствовании представлены новые действия XEvent и Фильтрация столбцов. Столбцы эквивалентны `query_hash` и `query_plan_hash`, за исключением того, что они определены как Int64. Определение INT64 помогает сопоставлять запросы между XE и DMV.
-   **Поддержка UTF-8 в BULK INSERT и bcp:** Это улучшение устраняет [Отзывы о подключении (370419)](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001). BULK INSERT и BCP теперь могут экспортировать или импортировать данные, закодированные в кодировке UTF-8.
-   **Упрощенное профилирование выполнения запроса для каждого оператора:** Инструкция Showplan предоставляет сведения о стоимости каждого оператора в плане. Но фактические статистические данные времени выполнения ограничены для таких задач, как ЦП, операции чтения ввода-вывода и прошедшее время на поток. SQL Server 2014 SP2 предоставляет дополнительные статистические данные о времени выполнения для каждого оператора в инструкции Showplan. Кроме того, в R2 введено приложение XEvent с именем `query_thread_profile` , помогающее устранить неполадки с производительностью запросов. Дополнительные [сведения см. в блоге](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/).
-   **Очистка отслеживание изменений:** Для очистки внутренних таблиц `sp_flush_CT_internal_table_on_demand` отслеживания изменений по требованию введена новая хранимая процедура.
-   **Ведение журнала времени ожидания аренды AlwaysON** Добавлена новая возможность ведения журнала для сообщений об истечении времени ожидания аренды, чтобы регистрировать текущее время и ожидаемое время продления. Кроме того, в журнал ошибок SQL появилось новое сообщение об истечении времени ожидания. Дополнительные [сведения см. в блоге](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/).
-   **Новые DMF для получения входного буфера в SQL Server:** Теперь доступен новый DMF для получения входного буфера для сеанса или запроса (sys. dm_exec_input_buffer). Этот DMF функционально эквивалентен DBCC INPUTBUFFER. Дополнительные [сведения см. в блоге](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/).
-   **Устранение недостаточных и неоцененных предоставлений памяти:** Добавлены новые указания запросов для Resource Governor с помощью MIN_GRANT_PERCENT и MAX_GRANT_PERCENT. Этот новый запрос позволяет использовать эти указания при выполнении запросов, ограничивая их предоставление памяти для предотвращения состязаний за память. Дополнительные сведения см. в [статье базы знаний KB310740](https://support.microsoft.com/kb/3107401).
-   **Улучшенная диагностика предоставления и использования памяти:** Новое расширенное событие с `query_memory_grant_usage` именем было добавлено в список возможностей трассировки в SQL Server. Это событие отслеживает запрошенные и предоставленные для памяти права. Это событие предоставляет улучшенные возможности трассировки и анализа для устранения любых проблем выполнения запросов, связанных с предоставлением памяти. Дополнительные сведения см. в [статье базы знаний KB3107173](https://support.microsoft.com/kb/3107173).
-   **Диагностика выполнения запросов для базы данных tempdb Spill:**— предупреждения хэша и сортировки теперь содержат дополнительные столбцы для мониторинга статистики физического ввода-вывода, используемой памяти и затронутых строк. Мы также представили новое расширенное событие hash_spill_details. Теперь вы можете отвести более детализированную информацию о хэшировании и предупреждениях сортировки ([KB3107172](https://support.microsoft.com/kb/3107172)). Кроме того, это улучшение можно получить с помощью планов XML-запросов в виде нового атрибута для сложного типа Спиллтотемпдбтипе ([KB3107400](https://support.microsoft.com/kb/3107400)). SET STATISTICS `ON` теперь показывает сортировку статистики рабочей таблицы.
-   **Улучшенная диагностика для планов выполнения запросов, использующих остаточный предикат включение:** Фактически считанные строки теперь передаются в планах выполнения запросов для улучшения производительности запросов. Эти строки отменяют необходимость записи набора СТАТИСТИЧЕСКИх операций ввода-вывода отдельно. Эти строки также позволяют просматривать сведения, относящиеся к остаточному предикату, в плане запроса. Дополнительные сведения см. в [статье базы знаний KB3107397](https://support.microsoft.com/kb/3107397).


## <a name="additional-information"></a>Дополнительные сведения  
 [Ресурсы по SQL Server 2014](../2014-toc/index.yml)  
  
 [SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [Центр ресурсов SQL Server 2014](https://msdn.microsoft.com/sqlserver/dn135309)  
  
 [Веб-сайт SQLCat](https://go.microsoft.com/fwlink/p/?linkID=220963)  
