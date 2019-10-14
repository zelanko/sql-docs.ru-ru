---
title: Новые возможности в SQL Server 2019 | Документация Майкрософт
ms.date: 08/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e85461ef0a6395904b0f80590a01f035eb51dc3a
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952760"
---
# <a name="whats-new-in-includesql-server-2019includessssqlv15-mdmd"></a>Новые возможности [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] основывается на предыдущих выпусках для расширения SQL Server как платформы, которая поддерживает ряд языков разработки, типов данных, операционных систем, а также работает в локальной и облачной средах.

В этой статье перечислены новые функции и усовершенствования для [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Дополнительные сведения и известные проблемы см. в статье с [заметками о выпуске предварительной версии [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](sql-server-ver15-release-notes.md).

**Используйте [новейшие средства](what-s-new-in-sql-server-ver15-prerelease.md#tools) для оптимальной работы с [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].**

>[!NOTE]
>Содержимое публикуется для релиз-кандидата [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. Релиз-кандидат — это предварительная версия программного обеспечения. Информация может быть изменена. Дополнительные сведения о сценариях поддержки см. в разделе о [поддержке](#support).
>
>Этот выпуск включает улучшения, о которых мы объявляли ранее в выпусках ознакомительной версии для сообщества. Такие улучшения включают новые функции, исправления ошибок, улучшенные функции безопасности и оптимизированную производительность. Список функций, реализованных или усовершенствованных в выпусках CTP, предшествующих релиз-кандидату [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], см. в [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]архиве объявлений CTP](what-s-new-in-sql-server-ver15-prerelease.md).

В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] появились [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] для [!INCLUDE[sql-server](../includes/ssnoversion-md.md)]. В этой версии также представлены дополнительные возможности и улучшения для ядра СУБД SQL Server, SQL Server Analysis Services, Служб машинного обучения SQL Server, SQL Server на Linux и SQL Server Master Data Services.

В следующих разделах приведены общие сведения о таких возможностях.

## <a name="data-virtualization-and-includebig-data-clusters-2019includesssbigdataclusters-ver15md"></a>Виртуализация данных и [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]

Сегодня предприятиям часто приходится полагаться на большие объемы данных из широкого спектра постоянно увеличивающихся наборов данных, размещенных в неконтролируемых источниках данных в компании. Вы можете получать ценную информацию практически в реальном времени из всех данных с помощью [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)], которые обеспечивают полномасштабную среду для работы с большими наборами данных, в том числе поддерживая машинное обучение и возможности искусственного интеллекта.

| Новые функции или обновления | Сведения |
|:---|:---|
| Масштабируемое решение для больших данных | [Развертывание масштабируемых кластеров](../big-data-cluster/deploy-get-started.md) SQL Server, Spark и контейнеров HDFS, работающих в Kubernetes <br/><br/> Чтение, запись и обработка больших данных из Transact-SQL или Spark<br/><br/> Простое объединение и анализ ценных реляционных данных и больших данных крупного объема<br/><br/>Запрос внешних источников данных<br/><br/>Хранение больших данных в HDFS под управлением SQL Server<br/><br/>Запрос данных из нескольких внешних источников данных через кластер<br/><br/> Использование данных для искусственного интеллекта, машинного обучения и других задач анализа<br/><br/> [Развертывание и запуск приложений](../big-data-cluster/concept-application-deployment.md) в [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] <br/><br/> Главный экземпляр SQL Server обеспечивает высокую доступность и аварийное восстановление для всех баз данных с помощью технологии группы доступности Always On.<br/>|
|Виртуализация данных через Polybase | Теперь вы можете запрашивать данные из внешних источников SQL Server, Oracle, Teradata, MongoDB и источников данных ODBC с внешними таблицами с поддержкой кодировки [UTF-8](../relational-databases/collations/collation-and-unicode-support.md). Дополнительные сведения см. в разделе [Что такое Polybase](../relational-databases/polybase/polybase-guide.md).|
| &nbsp; | &nbsp; |

Дополнительные сведения см. в разделе [What are SQL Server Big Data Clusters?[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]](../big-data-cluster/big-data-cluster-overview.md) (Что собой представляют кластеры больших данных SQL Server).

[[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Архив объявлений CTP](what-s-new-in-sql-server-ver15-prerelease.md) содержит список функций, объявленных и измененных во всех предыдущих выпусках CTP этой функции.

## <a name="intelligent-database"></a>Интеллектуальная база данных

### <a name="intelligent-query-processing"></a>Интеллектуальная обработка запросов

|Новые функции или обновления | Сведения |
|:---|:---|
|Обратная связь по временно предоставляемому буферу памяти в строковом режиме |Расширяет функцию обратной связи с временно предоставляемым буфером памяти в пакетном режиме путем настройки размеров временно предоставляемого буфера памяти для операторов пакетного и строкового режимов. Позволяет автоматически отменять излишние предоставленные разрешения, которые занимают память и снижают уровень параллелизма, а также решать проблемы, возникшие из-за недостатка временных буферов памяти. Такие проблемы влекут за собой чрезмерный расход ресурсов при записи на диск. См. раздел [Обратная связь по временно предоставляемому буферу памяти в строковом режиме](../relational-databases/performance/intelligent-query-processing.md#row-mode-memory-grant-feedback). |
|Отложенная компиляция табличных переменных|Оптимизирует план и повышает общую производительность запросов со ссылками на табличные переменные. Во время оптимизации и первичной компиляции эта функция распространяет оценки кратности, основанные на фактическом количестве строк табличной переменной. Эти точные сведения о количестве строк позволяют оптимизировать последующие операции плана. См. раздел [Отложенная компиляция табличных переменных](../relational-databases/performance/intelligent-query-processing.md#table-variable-deferred-compilation). |
|Приблизительная обработка запросов с помощью `APPROX_COUNT_DISTINCT `|Если не требуется абсолютная точность, но есть строгие требования ко времени реагирования, `APPROX_COUNT_DISTINCT` выполняет статистическое вычисление для крупных наборов данных, используя меньше ресурсов, чем `COUNT(DISTINCT())`, и обеспечивая намного лучший параллелизм. См. раздел [Приблизительная обработка запросов](../relational-databases/performance/intelligent-query-processing.md#approximate-query-processing).|
|Пакетный режим для данных rowstore|Пакетный режим для данных rowstore обеспечивает выполнение в пакетном режиме без необходимости использовать индексы columnstore. В пакетном режиме более эффективно используются ресурсы ЦП во время аналитических рабочих нагрузок. Но до версии [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] такая возможность использовалось, только если запрос включал операции с индексами columnstore. При этом некоторые приложения могут использовать функции, которые не поддерживают индексы columnstore и поэтому не работают в пакетном режиме. Начиная с версии [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] пакетный режим доступен для поддерживаемых рабочих нагрузок аналитики, запросы которых включают операции с любым типом индекса (rowstore или columnstore). См. раздел [Пакетный режим для данных rowstore](../relational-databases/performance/intelligent-query-processing.md#batch-mode-on-rowstore). |
|Встраивание скалярных пользовательских функций|Автоматически преобразует определяемые пользователем скалярные функции (UDF) в реляционные выражения и внедряет их в вызывающий SQL-запрос. Такое преобразование повышает производительность рабочих нагрузок, которые используют скалярные определяемые пользователем функции. См. раздел [Встраивание скалярных определяемых пользователем функций](../relational-databases/performance/intelligent-query-processing.md#scalar-udf-inlining).|
| &nbsp; | &nbsp; |


### <a name="in-memory-database"></a>Выполняющаяся в памяти база данных

|Новые функции или обновления | Сведения |
|:---|:---|
|Гибридный буферный пул| Новая возможность [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)], которая при необходимости обеспечивает прямой доступ к страницам базы данных, хранящимся в файлах базы данных и помещенным в устройство постоянной памяти (PMEM). См. статью [Гибридный буферный пул](../database-engine/configure-windows/hybrid-buffer-pool.md).|
|Оптимизированные для памяти метаданные `tempdb`| В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] появилась новая функция оптимизированных для памяти метаданных `tempdb`, входящая в семейство функций [выполняющейся в памяти базы данных](../relational-databases/in-memory-database.md). Она эффективно устраняет существующую проблему и открывает новый уровень масштабируемости для рабочих нагрузок, активно использующих `tempdb`. В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] системные таблицы, связанные с управлением метаданными временной таблицы, можно переместить в неустойчивые таблицы без кратковременной блокировки, оптимизированные для памяти. См. раздел [Оптимизированные для памяти метаданные `tempdb`](../relational-databases/databases/tempdb-database.md#memory-optimized-tempdb-metadata).|
| Поддержка выполняющейся в памяти OLTP для моментальных снимков базы данных | [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] предоставляет поддержку для создания [моментальных снимков баз данных](../relational-databases/databases/database-snapshots-sql-server.md), которые включают оптимизированные для памяти файловые группы. |
| &nbsp; | &nbsp; |

### <a name="intelligent-performance"></a>Интеллектуальная производительность

|Новые функции или обновления | Сведения |
|:---|:---|
|`OPTIMIZE_FOR_SEQUENTIAL_KEY`|Включает оптимизацию в [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)], что позволяет повысить пропускную способность для операций вставки в индекс с высокой степенью параллелизма. Этот параметр предназначен для индексов с состоянием состязания, возникающим при операциях вставки последней страницы (это характерно для индексов с последовательным ключом, включая столбец идентификаторов, последовательность или столбец даты и времени). См. подробнее о [CREATE INDEX](../t-sql/statements/create-index-transact-sql.md#sequential-keys).|
|Форсированная поддержка быстрых однопроходных и статических курсоров | План Query Store форсирует поддержку для перемотки вперед и статических курсоров. См. раздел [План форсирует поддержку для быстрых однопроходных и статических курсоров](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md#ctp23).|
|Управление ресурсами| Тип данных настраиваемого значения для параметра `REQUEST_MAX_MEMORY_GRANT_PERCENT` в `CREATE WORKLOAD GROUP` и `ALTER WORKLOAD GROUP` изменен с целого числа на число с плавающей точкой, что позволяет более точно контролировать ограничения памяти. Дополнительные сведения: [ALTER WORKLOAD GROUP](../t-sql/statements/alter-workload-group-transact-sql.md), [CREATE WORKLOAD GROUP](../t-sql/statements/create-workload-group-transact-sql.md).|
|Сокращение повторных компиляций для рабочих нагрузок| Улучшает использование временных таблиц в нескольких областях. См. раздел [Сокращение повторных компиляций для рабочих нагрузок](../relational-databases/tables/tables.md#ctp23). |
|Масштабируемость косвенных контрольных точек |См. раздел [Улучшена масштабируемость косвенных контрольных точек](../relational-databases/logs/database-checkpoints-sql-server.md#ctp23).|
|Одновременные обновления PFS|[Страницы PFS](https://techcommunity.microsoft.com/t5/SQL-Server/Under-the-covers-GAM-SGAM-and-PFS-pages/ba-p/383125) — это специальные страницы в файле базы данных, с помощью которых SQL Server находит свободное место при выделении пространства для объекта. Состязание за кратковременные блокировки страниц на страницах PFS обычно характерно для [`tempdb`](https://support.microsoft.com/en-us/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d). Но также оно может возникать в пользовательских базах данных при наличии большого количества параллельных потоков выделения объектов. Это улучшение позволяет изменить способ управления параллелизмом с помощью обновлений PFS, чтобы при этом можно было использовать общую кратковременную блокировку, а не монопольную блокировку. Это поведение включено по умолчанию во всех базах данных (включая `tempdb`) начиная с версии [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].|
| &nbsp; | &nbsp; |

### <a name="monitoring"></a>Наблюдение

|Новые функции или обновления | Сведения |
|:---|:---|
|`WAIT_ON_SYNC_STATISTICS_REFRESH` | Новый тип ожидания в динамическом административном представлении `sys.dm_os_wait_stats`. Он отображает суммарное время на уровне экземпляра, затраченное на синхронные операции обновления статистики. См. раздел [`sys.dm_os_wait_stats`](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|
|Пользовательская политика записи для хранилища запросов|Если этот параметр включен, для нового параметра политики записи хранилища запросов доступны дополнительные конфигурации хранилища запросов, что позволяет тонко настраивать сбор данных на конкретном сервере. Дополнительные сведения см. в описании [параметров ALTER DATABASE SET](../t-sql/statements/alter-database-transact-sql-set-options.md).|
|`LIGHTWEIGHT_QUERY_PROFILING`|Новая конфигурация области базы данных. См. раздел [`LIGHTWEIGHT_QUERY_PROFILING`](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#lqp). |
|`sys.dm_exec_requests` — столбец `command` | Отображает `SELECT (STATMAN)`, если `SELECT` ожидает завершения синхронной операции обновления статистики, прежде чем продолжить выполнение запроса. См. раздел [`sys.dm_exec_requests`](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|
|`sys.dm_exec_query_plan_stats` |Новая функция динамического управления возвращает эквивалент последнего известного действительного плана выполнения для большинства запросов. См. раздел [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md).|
|`LAST_QUERY_PLAN_STATS` | Новая конфигурация области базы данных для включения `sys.dm_exec_query_plan_stats`. В разделе [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|
|`query_post_execution_plan_profile` | Расширенное событие служит для сбора эквивалента действительного плана выполнения на основе упрощенного, а не стандартного профилирования, как в случае с событием `query_post_execution_showplan`. См. раздел [Инфраструктура профилирования запросов](../relational-databases/performance/query-profiling-infrastructure.md).|
|`sys.dm_db_page_info(database_id, file_id, page_id, mode)` | Новая функция динамического управления возвращает сведения о странице в базе данных. См. раздел [sys.dm_db_page_info (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md).|
| &nbsp; | &nbsp; |

## <a name="developer-experience"></a>Взаимодействие с разработчиками

### <a name="graph"></a>График

|Новые функции или обновления | Сведения |
|:---|:---|
|Действия каскадного удаления ограничений ребер |Определение каскадных действий удаления для ограничения ребер в базе данных графов. См. статью [Ограничения границ](../relational-databases/tables/graph-edge-constraints.md). |
|Новая функция графа: `SHORTEST_PATH` | Вы можете использовать `SHORTEST_PATH` в `MATCH` для поиска кратчайшего пути между любыми двумя узлами в графе или выполнения обходов произвольной длины.|
|Секционированные таблицы и индексы| Данные секционированных таблиц и индексов разделены на блоки, которые могут распределяться между несколькими файловыми группами в графовой базе данных. |
|Использование псевдонимов производной таблицы или представления для графовых запросов MATCH |См. статью [MATCH (Transact-SQL)](../t-sql/queries/match-sql-graph.md). |
| &nbsp; | &nbsp; |

### <a name="unicode-support"></a>Поддержка Юникода

|Новые функции или обновления | Сведения |
|:---|:---|
|Поддержка кодировки UTF-8 |Поддержка символов UTF-8 для импорта и экспорта кодировки, а также как параметров сортировки на уровне столбцов и базы данных для строковых данных. Это позволяет приложениям расширяться до глобального масштаба в тех случаях, когда для выполнения требований клиентов и определенных рыночных нормативов критически важно предоставлять глобальные многоязычные приложения баз данных и служб. См. раздел [Поддержка параметров сортировки и Юникода](../relational-databases/collations/collation-and-unicode-support.md).<br/><br/> Релиз-кандидат [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] включает поддержку UTF-8 для внешних таблиц Polybase и для Always Encrypted.|
| &nbsp; | &nbsp; |

### <a name="language-extensions"></a>Расширения языка

|Новые функции или обновления | Сведения |
|:---|:---|
|Новый SDK для языка Java | Упрощает разработку приложений Java, которые могут выполняться из SQL Server. См. статью о [пакете SDK Майкрософт для расширения возможностей Java в SQL Server](../language-extensions/how-to/extensibility-sdk-java-sql-server.md). |
|Пакет SDK для языка Java реализован с открытым кодом |[Пакет Microsoft SDK расширяемости для Java для Microsoft SQL Server](https://docs.microsoft.com/sql/language-extensions/how-to/extensibility-sdk-java-sql-server) теперь имеет открытый код и доступен [на GitHub](https://github.com/microsoft/sql-server-language-extensions).|
|Поддержка типов данных Java|См. раздел [Типы данных Java](../language-extensions/how-to/java-to-sql-data-types.md).|
|Новая среда выполнения Java по умолчанию | SQL Server теперь полностью поддерживает Zulu Embedded for Java от Azul Systems. Дополнительные сведения см. в статье [Теперь в SQL Server 2019 доступна бесплатная поддерживаемая версия Java](https://cloudblogs.microsoft.com/sqlserver/2019/07/24/free-supported-java-in-sql-server-2019-is-now-available/). |
|Расширения языка для SQL Server| Выполнение внешнего кода с помощью платформы расширяемости. См. статью о [расширении языка для SQL Server (предварительная версия)](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview).
|Регистрация внешних языков|Новый DDL `CREATE EXTERNAL LANGUAGE` регистрирует внешние языки, такие как Java, в SQL Server. См. раздел [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md). |
| &nbsp; | &nbsp; |

### <a name="spatial"></a>Пространственный

|Новые функции или обновления | Сведения |
|:---|:---|
| Новые идентификаторы пространственных ссылок (SRID) |[Australian GDA2020](http://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/datums-projections/gda2020) предоставляет более надежный и точный элемент данных, который в большей степени подходит для глобальных навигационных систем. Ниже приведены новые идентификаторы SRID:<br/><br/> - 7843 — географические двухмерные;<br/> - 7844 — географические трехмерные. <br/><br/>Представление [sys.spatial_reference_systems](../relational-databases/system-catalog-views/sys-spatial-reference-systems-transact-sql.md) содержит определения новых SRID. |
| &nbsp; | &nbsp; |

### <a name="error-messages"></a>Сообщения об ошибках

|Новые функции или обновления | Сведения |
|:---|:---|
|Подробные предупреждения об усечении | Сообщение об ошибке усечения по умолчанию включает имена таблицы и столбца, а также усеченное значение. См. раздел [VERBOSE_TRUNCATION_WARNINGS](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#verbose-truncation).|
| &nbsp; | &nbsp; |

## <a name="mission-critical-security"></a>Критически важный уровень безопасности

|Новые функции или обновления | Сведения |
|:---|:---|
|Always Encrypted с безопасными анклавами.|К Always Encrypted добавляется функция шифрования на месте и полнофункциональные вычисления, что позволяет выполнять вычисления с данными в виде обычного текста внутри безопасного анклава на стороне сервера. Шифрование на месте повышает производительность и надежность криптографических операций (шифрования столбцов, смены ключей шифрования столбцов и т. д.) благодаря тому, что данные не требуется перемещать за пределы базы данных. Поддержка многофункциональных вычислений (сопоставления шаблонов и операций сравнения) дает возможность использовать Always Encrypted в более широком спектре сценариев и приложений, которые требуют защиты конфиденциальных данных, а также более широкой функциональности в запросах Transact-SQL. См. подробнее об [использовании Always Encrypted с безопасными анклавами](../relational-databases/security/encryption/always-encrypted-enclaves.md).|
|Управление сертификатами в диспетчере конфигурации SQL Server.|См. статью [Управление сертификатами (диспетчер конфигурации SQL Server)](../database-engine/configure-windows/manage-certificates.md).|
| &nbsp; | &nbsp; |

## <a name="high-availability"></a>Высокий уровень доступности

### <a name="availability-groups"></a>Группы доступности

|Новые функции или обновления | Сведения |
|:---|:---|
|До пяти синхронных реплик|В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] максимальное количество синхронных реплик увеличено до пяти, по сравнению с тремя в [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Вы можете настроить эту группу из пяти реплик для автоматического перехода на другой ресурс в пределах группы. Предоставляется одна первичная реплика и четыре синхронные вторичные реплики.|
|Перенаправление подключения от вторичной реплики к первичной| Позволяет направлять подключения клиентских приложений к первичной реплике независимо от целевого сервера, указанного в строке подключения. Дополнительные сведения см. в статье [Перенаправление подключения с правами на чтение и запись с вторичной на первичную реплику (группы доступности AlwaysOn)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md).|
| &nbsp; | &nbsp; |

### <a name="recovery"></a>Восстановление

|Новые функции или обновления | Сведения |
|:---|:---|
|Ускоренное восстановление баз данных. | Ускорение восстановления базы данных (ADR) для отдельных баз данных. См. раздел [Ускоренное восстановление баз данных](../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#adr).|
| &nbsp; | &nbsp; |

### <a name="resumable-operations"></a>Возобновляемые операции

|Новые функции или обновления | Сведения |
|:---|:---|
|Сборка и перестроение кластеризованных индексов columnstore в режиме "в сети" | См. раздел [Выполнение операций с индексами в режиме "в сети"](../relational-databases/indexes/perform-index-operations-online.md). |
|Возобновляемая сборка индексов rowstore в режиме "в сети" | См. раздел [Выполнение операций с индексами в режиме "в сети"](../relational-databases/indexes/perform-index-operations-online.md). |
|Приостановка и возобновление начального сканирования прозрачного шифрования данных (TDE)|См. раздел [Сканирование — прозрачное шифрование данных (TDE)](../relational-databases/security/encryption/transparent-data-encryption.md#scan-suspend-resume).|
| &nbsp; | &nbsp; |

## <a name="setup"></a>Настройка 

|Новые функции или обновления | Сведения | 
|:---|:---| 
|Новые параметры настройки памяти | Задает конфигурации *минимальной памяти сервера (МБ)* и *максимальной памяти сервера (МБ)* во время установки. Дополнительные сведения см. в статье [Справка по мастеру установки](https://docs.microsoft.com/sql/sql-server/install/instance-configuration?view=sql-server-ver15#memory), а также в описаниях параметров `USESQLRECOMMENDEDMEMORYLIMITS`, `SQLMINMEMORY` и `SQLMAXMEMORY` в разделе [Параметры установки](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#Install). Предложенное значение будет соответствовать рекомендациям по настройке памяти, приведенным в разделе [Настройка параметров памяти вручную](../database-engine/configure-windows/server-memory-server-configuration-options.md#setting-the-memory-options-manually).| 
|Новые параметры настройки параллелизма | Задает параметр *максимального уровня параллелизма* во время установки. Дополнительные сведения см. в статье [Справка по мастеру установки](https://docs.microsoft.com/sql/sql-server/install/instance-configuration?view=sql-server-ver15#maxdop) и в описании параметра `SQLMAXDOP` в разделе [Параметры установки](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#Install). Значение по умолчанию будет соответствовать рекомендациям по максимальной степени параллелизма, приведенным в разделе [Рекомендации](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines).| 
| &nbsp; | &nbsp; |

## <a name="platform-choice"></a>Вариант платформы

### <a id="sql-server-on-linux"></a>Linux

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Новый реестр контейнеров.|[Начало работы с контейнерами SQL Server в Docker](../linux/quickstart-install-connect-docker.md) |
|Поддержка репликации. |[Репликация SQL Server в Linux](../linux/sql-server-linux-replication.md)
|Поддержка координатора распределенных транзакций Майкрософт (MSDTC). |[Настройка MSDTC на платформе Linux](../linux/sql-server-linux-configure-msdtc.md) |
|Поддержка OpenLDAP для сторонних поставщиков Active Directory. |[Учебник. Использование проверки подлинности Azure Active Directory с SQL Server на Linux](../linux/sql-server-linux-active-directory-authentication.md) |
|Поддержка машинного обучения в Linux. |[Настройка машинного обучения в Linux](../linux/sql-server-linux-setup-machine-learning.md) |
|Улучшения `tempdb` | По умолчанию новая установка SQL Server на Linux создает несколько файлов данных `tempdb` на основе числа логических ядер (до 8 файлов данных). Это не применимо к обновлениям основной или дополнительной версии на месте. Размер каждого файла `tempdb` составляет 8 МБ с возможностью автоматического увеличения до 64 МБ. Это поведение аналогично поведению установки SQL Server по умолчанию в Windows. |
| PolyBase на компьютерах под управлением Linux | [Установка PolyBase](../relational-databases/polybase/polybase-linux-setup.md) в Linux для соединителей вне Hadoop.<br/><br/>[Сопоставление типов PolyBase](../relational-databases/polybase/polybase-type-mapping.md). |
| Поддержка системы отслеживания измененных данных (CDC) | Система отслеживания измененных данных (CDC) теперь поддерживается в Linux для SQL Server 2019. |
| &nbsp; | &nbsp; |

### <a name="containers"></a>Контейнеры

|Новые функции или обновления | Сведения |
|:---|:---|
| Реестр контейнеров Майкрософт | [Реестр контейнеров Майкрософт](https://www.ntweekly.com/2019/09/23/microsoft-container-registry-to-replace-docker-hub-for-new-images/) теперь заменяет Docker Hub в качестве источника новых официальных образов контейнеров Майкрософт, включая [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. |
| Непривилегированные контейнеры | [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] предоставляет возможность создания более безопасных контейнеров путем запуска процесса [!INCLUDE[sql-server](../includes/ssnoversion-md.md)] по умолчанию от имени пользователя, не являющегося привилегированным. См. раздел [Сборка и запуск контейнеров SQL Server от имени непривилегированного пользователя](../linux/sql-server-linux-configure-docker.md#buildnonrootcontainer). |
| &nbsp; | &nbsp; |

## <a id="ml"></a> Службы машинного обучения SQL Server

|Новые функции или обновления | Сведения |
|:---|:---|
|Моделирование на основе разделов|Обработка внешних сценариев на каждый раздел данных с использованием новых параметров, добавленных в `sp_execute_external_script`. Эта функция поддерживает обучение нескольких небольших моделей (одна модель на раздел данных) вместо одной большой. См. раздел [Создание моделей на основе секций](../advanced-analytics/tutorials/r-tutorial-create-models-per-partition.md)|
|Отказоустойчивый кластер Windows Server| Настройка высокого уровня доступности для Служб машинного обучения в отказоустойчивом кластере Windows Server.|
| &nbsp; | &nbsp; |

## [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]

| Новые функции или обновления | Сведения |
|:---|:---|
|Поддерживает базы данных управляемого экземпляра базы данных SQL Azure.| Размещение [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] на управляемом экземпляре. См. раздел [Установка и настройка [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]](../master-data-services/master-data-services-installation-and-configuration.md#SetUpWeb).|
|Новые элементы управления HTML| Элементы управления HTML заменяют все бывшие компоненты Silverlight. Зависимость от Silverlight устранена.|
| &nbsp; | &nbsp; |

## <a name="sql-server-analysis-services"></a>службы SQL Server Analysis Services

| Новые функции или обновления | Сведения |
|:---|:---|
|Чередование запросов| См. статью о [чередовании запросов](https://docs.microsoft.com/analysis-services/tabular-models/query-interleaving). |
|Поддержка запросов многомерных выражений для табличных моделей с использованием групп вычислений | См. раздел [Группы вычисления](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24). |
|Группы вычисления в табличных моделях| [Группы вычисления в табличных моделях](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24) |
|Поддержка запросов многомерных выражений для табличных моделей с использованием групп вычислений | См. раздел [Группы вычисления](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24). |
|Динамическое форматирование мер с помощью групп вычислений |Эта функция позволяет условно изменять строки формата для мер с помощью [групп вычислений](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24). Например, благодаря преобразованию валюты меры можно отобразить с использованием разных форматов иностранных валют.|
|Связи "многие ко многим" в табличных моделях|[Связи "многие ко многим" в табличных моделях](what-s-new-in-sql-server-ver15-prerelease.md#many-to-many-ctp24)|
|Настройка свойств для регуляции ресурсов|[Настройка свойств для регуляции ресурсов](what-s-new-in-sql-server-ver15-prerelease.md#property-ctp24)|
| Параметр управления для обновлений кэша Power BI.  | Служба Power BI кэширует данные плиток панелей мониторинга и отчетов для начальной загрузки отчетов Live Connect, что приводит к чрезмерному увеличению числа запросов кэша к службам SSAS, и в экстремальных случаях сервер оказывается перегружен. В этом выпуске вводится свойство **ClientCacheRefreshPolicy**. Оно позволяет переопределить это поведение на уровне сервера. Дополнительные сведения см. в разделе [Общие свойства](https://docs.microsoft.com/analysis-services/server-properties/general-properties). |
| Интерактивное подключение  | Эта функция предоставляет возможность присоединить табличную модель в интерактивном режиме. Такое подключение можно использовать для синхронизации реплик только для чтения в локальных средах масштабирования запросов. Дополнительные сведения см. в разделе [Интерактивное подключение](what-s-new-in-sql-server-ver15-prerelease.md#online-attach-ctp32). |
| &nbsp; | &nbsp; |

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

Описание конкретных функций, исключенных из программы поддержки, см. в [заметках о выпуске](sql-server-ver15-release-notes.md).

Кроме того, в версии [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 3.2 добавлены или улучшены следующие функции.

## <a name="see-also"></a>См. также раздел

- [`SqlServer` Модуль PowerShell](https://www.powershellgallery.com/packages/Sqlserver)
- [Документация по SQL Server PowerShell](../powershell/sql-server-powershell.md)

## <a name="next-steps"></a>Следующие шаги

- [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]: заметки о выпуске](sql-server-ver15-release-notes.md).

- [Майкрософт [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]: Технический документ](http://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Опубликовано в сентябре 2018 г. Применяется к CTP-версии 2.0 Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] для контейнеров Windows, Linux и Docker.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
