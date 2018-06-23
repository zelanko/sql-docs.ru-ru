---
title: Что&#39;новые возможности SQL Server 2014 | Документы Microsoft
ms.custom: ''
ms.date: 05/25/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- database-engine
- integration-services
- master-data-services
- replication
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- new features [SQL Server]
- SQL Server, what's new
- SQL Server 2008 what's new
- what's new [SQL Server]
- sql server 2014 sp1
- sql server 2014 sp2
ms.assetid: 6a428023-e3cc-4626-a88a-4c13ccbd7db0
caps.latest.revision: 70
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9144eeb653649e36cfed3551e4ec465d403ffdcb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097648"
---
# <a name="what39s-new-in-sql-server-2014"></a>Что&#39;новые возможности SQL Server 2014
  В этом разделе приведены подробные ссылки на новые функции в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] и приводится краткое описание пакеты служб для [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 
**Попробуйте продукт:** ![виртуальной машине Azure малых](./media/what-s-new-in-sql-server-2016/azure-virtual-machine-small.png) есть учетная запись Azure?  Затем перейдите **[здесь](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2014sp1EnterpriseWindowsServer2012R2)** для раскрутки виртуальную машину с SQL Server 2014 с пакетом обновления 1 (SP1) уже установлена. 
  
-   [Новые возможности &#40;компонент Database Engine&#41;](../database-engine/whats-new-in-sql-server-2016.md)  
  
-   [Новые возможности служб Analysis Services и бизнес-аналитики](../analysis-services/what-s-new-in-analysis-services.md)  
  
-   [Новые возможности установки SQL Server](install/what-s-new-in-sql-server-installation.md)  
  
 **[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] не внес важных новых функций следующее:**  
  
-   [Новые возможности &#40;службы Integration Services&#41;](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)  
  
-   [Новые возможности &#40;репликации&#41;](../relational-databases/replication/what-s-new-replication.md)  
  
-   [Новые возможности &#40;службы Reporting Services&#41;](../reporting-services/what-s-new-reporting-services.md)  
  
## <a name="includesssql14includessssql14-mdmd-service-pack-1-sp1"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] с пакетом обновления 1 (SP1)
[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP1) не удалось вызвать важных новых функций.
-  [Замечания к выпуску SQL Server 2014 с пакетом обновления 1 ](https://support.microsoft.com/en-us/kb/3058865).
-  [![Загрузите пакет обновления 1 для Microsoft® SQL Server® 2014](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=46694) [загрузить пакет обновления 1 для Microsoft® SQL Server® 2014](https://www.microsoft.com/en-us/download/details.aspx?id=46694).


## <a name="includesssql14includessssql14-mdmd-service-pack-2-sp2"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Пакет обновления 2 (SP2)
- [Замечания к выпуску SQL Server 2014 с пакетом обновления 2](https://support.microsoft.com/en-us/kb/3171021).
-  [![Загрузить пакет обновления 2 для SQL Microsoft® Server® 2014](./media/what-s-new-in-sql-server-2016/download.png)](http://go.microsoft.com/fwlink/?LinkID=821558) [загрузить пакет обновления 2 для SQL Microsoft® Server® 2014](http://go.microsoft.com/fwlink/?LinkID=821558).
-  [![Загрузите пакет дополнительных компонентов SQL Server 2014 SP2](./media/what-s-new-in-sql-server-2016/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=53164) [загрузки пакета дополнительных компонентов SQL Server 2014 SP2](https://www.microsoft.com/en-us/download/details.aspx?id=53164).

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] (SP2) Включает следующие улучшения:

### <a name="performance-and-scalability-improvements"></a>Производительность и усовершенствования масштабируемости 
-   **Автоматическое создание разделов программная архитектура NUMA:** с [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2, автоматическое программная архитектура NUMA включен, при включении 8079 флаг трассировки во время запуска экземпляра. При включении 8079 флаг трассировки во время запуска, [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 будет опроса макета оборудования и автоматически настроить программная архитектура NUMA в системах reporting 8 и более процессоров на узел NUMA. Автоматическое, мягкое поведение NUMA не учитывать Hyperthread (HT или логическим процессором). Секционирование и создание дополнительных узлов позволяет масштабировать фоновую обработку за счет увеличения числа прослушивателей и масштаба вычислений, а также расширения возможностей сети и шифрования. Рекомендуется первый тест производительности рабочей нагрузки с Auto Soft NUMA перед включением его в рабочей среде. [См. Дополнительные сведения в записи](https://blogs.msdn.microsoft.com/psssql/2016/03/30/sql-2016-it-just-runs-faster-automatic-soft-numa/). 
-  **Динамическое масштабирование объекта памяти:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 динамически секции объекты памяти в зависимости от числа узлов и ядер для масштабирования на современном оборудовании. Динамическое повышение предназначена для автоматического секционирования объект безопасном память потока (CMEMTHREAD), если он становится узким местом. Объекты памяти разбиты на секции может быть повышен динамически разделяемый узлом (количество секций равно количество узлов NUMA) и памяти объектов, секционирована по узел можно путем продолжить повышены до секционированы по ЦП (количество секций равно ЦП). [См. Дополнительные сведения в записи](https://blogs.msdn.microsoft.com/psssql/2016/04/06/sql-2016-it-just-runs-faster-dynamic-memory-object-cmemthread-partitioning/).
-  **Подсказки MAXDOP для команды DBCC CHECK\* команды:** это улучшение адреса [подключения обратной связи (468694)](https://connect.microsoft.com/SQLServer/feedback/details/468694/maxdop-option-in-dbcc-checkdb). Теперь можно запустить инструкцию DBCC CHECKDB с параметр MAXDOP, отличному от значения хранимой процедуры sp_configure. Если MAXDOP превышает значение, настроенное с помощью Resource Governor, ядро СУБД использует значение MAXDOP из Resource Governor, как описано в статье "ALTER WORKLOAD GROUP (Transact-SQL)". Все семантические правила, используемые параметром конфигурации max degree of parallelism, применимы при использовании указания запроса MAXDOP. Дополнительные сведения см. в разделе [DBCC CHECKDB (Transact-SQL)](https://msdn.microsoft.com/library/ms176064.aspx).
-   **Включить > 8 ТБ для буферного пула:** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 включает 128 ТБ виртуального адресного пространства для использование буферного пула. Это улучшение позволяет SQL Server буферного пула, выполнить масштабирование свыше 8 ТБ на современном оборудовании.
-   **Spinlock SOS_RWLock улучшения:** SOS_RWLock — это примитив синхронизации, используемые в разных местах базу кода в SQL Server.  Как следует из имен, код может иметь несколько общих (чтения) или владения одним (записи). Это улучшение избавляет spinlock для SOS_RWLock и вместо этого использует методы без блокировки аналогично OLTP в памяти. Это изменение числа потоков может считывать структуру данных, защищенных SOS_RWLock параллельно без блокировки друг с другом и тем самым обеспечивая более высокую масштабируемость. До этого изменения реализации spinlock допускается только один поток для получения SOS_RWLock одновременно, даже для чтения структуру данных.  [См. Дополнительные сведения в записи](https://blogs.msdn.microsoft.com/psssql/2016/04/07/sql-2016-it-just-runs-faster-sos_rwlock-redesign/).
-    **Пространственные собственную реализацию:** значительный прирост производительности пространственных впервые появился в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP2 через собственную реализацию. Дополнительные сведения см. в разделе [статьи базы знаний KB3107399](https://support.microsoft.com/en-us/kb/3107399).

### <a name="supportability-and-diagnostics-improvements"></a>Средства поддержки и усовершенствования диагностики
-   **Клонирование базы данных:** клонированной базы данных является новой команды DBCC, расширяющий возможности устранения неполадок существующих рабочих баз данных путем копирования схемы и метаданных без данных. Копия создается с помощью команды `DBCC clonedatabase(‘source_database_name’, ‘clone_database_name’)`.  **Примечание:** Cloned баз данных не должны использоваться в производственной среде. Выполните следующую команду, определить, если базы данных был создан из точная копия базы данных: `select DATABASEPROPERTYEX('clonedb', 'isClone')`. Возвращаемое значение **1** указывает база данных создается из clonedatabase при **0** указывает не клон.
-   **Поддержка базы данных tempdb:** новый журнал ошибок сообщение, указывающее число файлов tempdb и размер авторасширение данных tempdb файлы присутствуют при запуске сервера.
-   **Базы данных мгновенную инициализацию ведение журнала:** новый журнал ошибок сообщение, указывающее на statup сервера, состояние Мгновенная инициализация файлов базы данных (Включение или отключение).
-   **Имена модулей в стек вызовов:** Xevent callstack теперь включает имена модулей + смещение, а не абсолютных адресов.
-   **Новый DMF для добавочной статистики:** это улучшение адреса [подключения обратной связи (797156)](https://connect.microsoft.com/SQLServer/feedback/details/797156/display-sys-dm-db-stats-properties-per-partition-for-incremental-statistics) для включения отслеживания добавочные статистические данные на уровне секции. Для предоставления сведений в секцию для добавочные статистики введен новый sys.dm_db_incremental_stats_properties DMF.
-   **Поведение динамического административного Представления об использовании индекса обновлен:** это улучшение адреса [подключения обратной связи (739566)](https://connect.microsoft.com/SQLServer/feedback/details/739566/rebuilding-an-index-clears-stats-from-sys-dm-db-index-usage-stats) от клиентов, где будет перестроения индекса *не* удаления любой существующей строки из sys.dm_db _index_usage_stats для этого индекса. Поведение теперь будет такой же, как SQL 2008 и SQL Server 2016. [См. Дополнительные сведения в записи](https://blogs.msdn.microsoft.com/sql_server_team/index-usage-dmv-behavior-updated/).
-   **Улучшенная корреляции между XE диагностику и динамические административные представления:** это улучшение адреса [подключения обратной связи (1934583)](https://connect.microsoft.com/SQLServer/feedback/details/1934583/extended-events-query-hash-and-query-plan-hash-data-types). Значения Query_hash и фиксировать используются для определения запроса, уникальным образом. Динамическое административное представление определяет их как varbinary(8), а XEvent определяет их как UINT64. Поскольку SQL server не имеет «unisigned bigint», приведения типов не всегда работает. Данное улучшение представляет новые столбцы действий и фильтров XEvent, эквивалентные query_hash и query_plan_hash, но определяемые как INT64. Это может помочь в корреляции запросов между событиями XE и динамическими административными представлениями.
-   **Поддержка UTF-8 в инструкции BULK INSERT и BCP:** это улучшение адреса [подключения обратной связи (370419)](https://connect.microsoft.com/SQLServer/feedback/details/370419/bulk-insert-and-bcp-does-not-recognize-codepage-65001) где в инструкции BULK INSERT и BCP теперь включена поддержка экспорта и импорта данных, закодированы в кодировке UTF-8.
-   **Профилирование выполнения запроса упрощенных оператор:** при устранении неполадок производительности запросов, несмотря на то, что инструкции showplan содержит большой объем сведений о плана выполнения запроса и стоимость оператора в плане, но он имеет ограниченные сведения о фактических статистические данные времени выполнения, как (ЦП, ввода-вывода считывает, затраченное время каждого потока). SQL 2014 SP2 предоставляет статистику дополнительных среды выполнения каждого оператора в инструкции Showplan, а также XEvent (query_thread_profile) для устранения неполадок производительности запросов. [См. Дополнительные сведения в записи](https://blogs.msdn.microsoft.com/sql_server_team/added-per-operator-level-performance-stats-for-query-processing/).
-   **Очистки отслеживания изменений:** новая хранимая процедура `sp_flush_CT_internal_table_on_demand` введен для очистки отслеживания изменений внутренних таблиц в запросу.
-   **Ведение журнала времени ожидания аренды AlwaysON** добавлен новый возможность ведения журнала для сообщения времени ожидания аренды, что текущее время и время продления ожидаемый регистрируются. Также новое сообщение появилась в SQL Errorlog относительно времени ожидания. [См. Дополнительные сведения в записи](https://blogs.msdn.microsoft.com/alwaysonpro/2016/02/23/improved-alwayson-availability-group-lease-timeout-diagnostics/).
-   **Новый DMF для извлечения входной буфер в SQL Server:** новый DMF для извлечения из входного буфера для сеанса или запроса (sys.dm_exec_input_buffer) теперь доступен. Она функционально эквивалентна команде DBCC INPUTBUFFER. [См. Дополнительные сведения в записи](https://blogs.msdn.microsoft.com/sql_server_team/new-dmf-for-retrieving-input-buffer-in-sql-server/).
-   **Устранение рисков для предоставления памяти недооценивают и overestimated:** добавлены новые подсказки в запросах для регулятора ресурсов через MIN_GRANT_PERCENT и MAX_GRANT_PERCENT. Это позволяет использовать эти подсказки при выполнении запросов путем ограничения предоставление памяти, чтобы предотвратить конфликты памяти. Дополнительные сведения см. в разделе [статьи базы знаний KB310740](https://support.microsoft.com/en-us/kb/3107401)
-   **Более высокий уровень диагностики для предоставления и использования памяти:** новых расширенных событий был добавлен к списку возможности трассировки в SQL Server (query_memory_grant_usage) для отслеживания памяти предоставляет запрашиваются и предоставляются. Это обеспечивает повышения возможности трассировки и анализа для устранения неполадок выполнения запросов, связанных с выделения памяти. Дополнительные сведения см. в разделе [статьи базы знаний KB3107173](https://support.microsoft.com/en-us/kb/3107173).
-   **Запрос выполнения диагностики для временной базы данных tempdb:**-Hash Warning и Sort Warnings теперь имеют дополнительные столбцы для отслеживания физического ввода-вывода статистики, память, используемая и обработанных строк. Мы также представили новый расширенных событий hash_spill_details. Теперь можно отслеживать более подробные сведения для предупреждений, хэширования и сортировки ([KB3107172](https://support.microsoft.com/en-us/kb/3107172)). Это улучшение теперь также предоставляется с помощью планов запросов XML в виде нового атрибута в сложный тип SpillToTempDbType ([KB3107400](https://support.microsoft.com/en-us/kb/3107400)). Задать статистики теперь показывает сортировки статистики рабочей таблицы. , и делает это по-другому.
-   **Улучшенная Диагностика для планов выполнения запросов, включающих Включение остаточного предиката:** фактические строки, считанные теперь должны отображаться в плане выполнения запроса, чтобы помочь улучшить устранению проблем производительности запросов. Это следует поставить под сомнение необходимость отслеживания SET STATISTICS IO отдельно. Теперь можно просмотреть сведения, относящиеся к остаточные Включение предиката в плане запроса. Дополнительные сведения см. в разделе [статьи базы знаний KB3107397](https://support.microsoft.com/en-us/kb/3107397).


## <a name="additional-information"></a>Дополнительные сведения  
 [Ресурсы по SQL Server 2014](../2014-toc/books-online-for-sql-server-2014.md)  
  
 [SQL Server 2014 Release Notes](http://go.microsoft.com/fwlink/p/?linkID=296445)  
  
 [Центр ресурсов SQL Server 2014](http://msdn.microsoft.com/sqlserver/dn135309)  
  
 [Веб-сайт SQLCat](http://go.microsoft.com/fwlink/p/?linkID=220963)  
  
  