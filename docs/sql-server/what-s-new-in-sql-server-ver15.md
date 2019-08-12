---
title: Новые возможности в SQL Server 2019 | Документация Майкрософт
ms.date: 07/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: bfe22edbc76805fb821ddda42a07a3b74395bdb6
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893991"
---
# <a name="whats-new-in-includesql-server-2019includessssqlv15-mdmd"></a>Новые возможности [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] основывается на предыдущих выпусках для расширения SQL Server как платформы, которая поддерживает ряд языков разработки, типов данных, операционных систем, а также работает в локальной и облачной средах.

В этой статье перечислены новые функции и усовершенствования для [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Дополнительные сведения и известные проблемы см. в статье с [заметками о выпуске предварительной версии [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](sql-server-ver15-release-notes.md).

**Используйте [новейшие средства](what-s-new-in-sql-server-ver15-prerelease.md#tools) для оптимальной работы с [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].**

## <a name="ctp-32-july-2019"></a>CTP 3.2 — июль 2019 г.

Ознакомительная версия для сообщества (CTP) 3.2 — это последний общедоступный выпуск [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. Этот выпуск включает усовершенствования предыдущих выпусков CTP для исправления ошибок, повышения безопасности и оптимизации производительности. Список функций, появившихся или усовершенствованных в каждом из выпусков CTP, предшествующих CTP-версии [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] 3.2, см. в [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]архиве объявлений CTP](what-s-new-in-sql-server-ver15-prerelease.md).

### <a name="new-in-big-data-clusters"></a>Новые возможности для кластеров больших данных

|Новые функции или обновления | Сведения |
|:---|:---|
|Общедоступная предварительная версия |До CTP-версии 3.2 кластер больших данных SQL Server был доступен для зарегистрированных ранних последователей. Этот выпуск позволяет любому пользователю работать с кластерами больших данных SQL Server. <br/><br/> См. статью [Начало работы с кластерами больших данных SQL Server](../big-data-cluster/deploy-get-started.md).|
|`azdata` |В CTP 3.2 представлена `azdata` — служебная программа командной строки на языке Python, которая позволяет администраторам кластера провести начальную загрузку и управлять кластером больших данных с помощью интерфейсов API. `azdata` заменяет собой `mssqlctl`. См. раздел [Установка `azdata`](../big-data-cluster/deploy-install-azdata.md). |
|PolyBase |Имена столбцов внешней таблицы теперь используются для запроса источников данных SQL Server, Oracle, Teradata, MongoDB и ODBC. В предыдущих выпусках CTP столбцы были привязаны только по порядковому номеру назначения, а имена столбцов в определении внешней таблицы не использовались.|
|Обновление распределения по уровням HDFS |Представлена функция обновления для распределения по уровням HDFS, чтобы можно было обновить существующее подключение на основе последнего моментального снимка удаленных данных. См. раздел [Распределение по уровням HDFS](../big-data-cluster/hdfs-tiering.md). |
|Устранение неполадок на основе записных книжек |В CTP 3.2 введены записные книжки Jupyter для помощи в [развертывании](../big-data-cluster/deploy-notebooks.md) и [обнаружении, диагностике и устранении неполадок](../big-data-cluster/manage-notebooks.md) для компонентов кластера больших данных SQL Server. |
| &nbsp; | &nbsp; |

### <a name="new-in-analysis-services"></a>Новые возможности в службах Analysis Services

| Новые функции или обновления | Сведения |
|:---|:---| 
| Параметр управления для обновлений кэша Power BI.  | Служба Power BI кэширует данные плиток панелей мониторинга и отчетов для начальной загрузки отчетов Live Connect, что приводит к чрезмерному увеличению числа запросов кэша к службам SSAS, и в экстремальных случаях сервер оказывается перегружен. В этом выпуске вводится свойство **ClientCacheRefreshPolicy**. Оно позволяет переопределить это поведение на уровне сервера. Дополнительные сведения см. в разделе [Общие свойства](https://docs.microsoft.com/analysis-services/server-properties/general-properties). |
| Интерактивное подключение  | Эта функция предоставляет возможность присоединить табличную модель в интерактивном режиме. Такое подключение можно использовать для синхронизации реплик только для чтения в локальных средах масштабирования запросов. Дополнительные сведения см. в разделе [Интерактивное подключение](what-s-new-in-sql-server-ver15-prerelease.md#online-attach-ctp32). |
| &nbsp; | &nbsp; |

### <a name="new-in-language-extensions"></a>Новые расширения языка

|Новые функции или обновления | Сведения |
|:---|:---|
| Новая среда выполнения Java по умолчанию  | SQL Server теперь включает поддержку Zulu Embedded for Java от Azul System во всем продукте. Дополнительные сведения см. в статье [Теперь в SQL Server 2019 доступна бесплатная поддерживаемая версия Java](https://cloudblogs.microsoft.com/sqlserver/2019/07/24/free-supported-java-in-sql-server-2019-is-now-available/). |

### <a name="new-in-sql-server-on-linux"></a>Новые возможности SQL Server в Linux

|Новые функции или обновления | Сведения |
|:---|:---|
| Поддержка системы отслеживания измененных данных (CDC) | Система отслеживания измененных данных (CDC) теперь поддерживается в Linux для SQL Server 2019. |

## <a name="includesql-server-2019includessssqlv15-mdmd-features-by-component"></a>Функции [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] по компонентам

В следующих разделах описаны новые компоненты и функции, которые были улучшены в предыдущих выпусках [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

## <a name="big-data-clusters"></a>Кластеры больших данных

| Новые функции или обновления | Сведения |
|:---|:---|
| Масштабируемое решение для больших данных | [Развертывание масштабируемых кластеров](../big-data-cluster/deploy-get-started.md) SQL Server, Spark и контейнеров HDFS, работающих в Kubernetes <br/><br/> Чтение, запись и обработка больших данных из Transact-SQL или Spark<br/><br/> Простое объединение и анализ ценных реляционных данных и больших данных крупного объема<br/><br/>Запрос внешних источников данных<br/><br/>Хранение больших данных в HDFS под управлением SQL Server<br/><br/>Запрос данных из нескольких внешних источников данных через кластер<br/><br/> Использование данных для искусственного интеллекта, машинного обучения и других задач анализа<br/><br/> Развертывание и запуск приложений в кластерах больших данных <br/>|
| &nbsp; | &nbsp; |

Дополнительные сведения см. в разделе [Что такое кластеры больших данных SQL Server](../big-data-cluster/big-data-cluster-overview.md)

[[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Архив объявлений CTP](what-s-new-in-sql-server-ver15-prerelease.md) содержит список функций, объявленных и измененных во всех предыдущих выпусках CTP этой функции.

## <a name="database-engine"></a>Ядро СУБД

### <a name="security"></a>безопасность

|Новые функции или обновления | Сведения |
|:---|:---|
|Ограничения функций| Предотвращение утечки сведений о базе данных при атаках путем внедрения кода SQL даже в том случае, если внедрение кода SQL выполнено успешно. См. раздел [Ограничения функций](../relational-databases/security/feature-restrictions.md)|
|Индексирование зашифрованных столбцов|Вы можете индексировать столбцы, зашифрованные с помощью случайного шифрования и ключей с поддержкой анклава, чтобы повысить производительность полнофункциональных запросов (с помощью операторов `LIKE` и операторов сравнения). См. подробнее об [использовании Always Encrypted с безопасными анклавами](../relational-databases/security/encryption/always-encrypted-enclaves.md).
|Приостановка и возобновление начального сканирования прозрачного шифрования данных (TDE)|См. раздел [Приостановка и возобновление сканирования прозрачного шифрования данных (TDE)](../relational-databases/security/encryption/transparent-data-encryption.md#scan-suspend-resume)|
|Управление сертификатами в диспетчере конфигурации SQL Server.|См. раздел [Управление сертификатами (диспетчер конфигурации SQL Server)](../database-engine/configure-windows/manage-certificates.md)
| &nbsp; | &nbsp; |


### <a name="graph"></a>График

|Новые функции или обновления | Сведения |
|:---|:---|
|Действия каскадного удаления ограничений ребер |Определение каскадных действий удаления для ограничения ребер в базе данных графов. См. раздел [Ограничения ребер](../relational-databases/tables/graph-edge-constraints.md). |
|Новая функция графа: `SHORTEST_PATH` | Вы можете использовать `SHORTEST_PATH` в `MATCH` для поиска кратчайшего пути между любыми двумя узлами в графе или выполнения обходов произвольной длины.|
|Секционированные таблицы и индексы| Данные секционированных таблиц и индексов разделены на блоки, которые могут распределяться между несколькими файловыми группами в графовой базе данных. |
|Использование псевдонимов производной таблицы или представления для графовых запросов MATCH |См. раздел [Ограничения ребер графа](../relational-databases/tables/graph-edge-constraints.md). |
| &nbsp; | &nbsp; |

### <a name="indexes"></a>Индексы

|Новые функции или обновления | Сведения |
|:---|:---|
|`OPTIMIZE_FOR_SEQUENTIAL_KEY`|Включение оптимизации в ядре СУБД, что позволяет повысить пропускную способность для операций вставки с высокой степенью параллелизма в индекс. Этот параметр предназначен для индексов с состоянием состязания, возникающим при операциях вставки последней страницы (это характерно для индексов с последовательным ключом, включая столбец идентификаторов, последовательность или столбец даты и времени). См. подробнее о [CREATE INDEX](../t-sql/statements/create-index-transact-sql.md#sequential-keys).|
|Сборка и перестройка кластеризованных индексов columnstore в подключенном режиме. | См. раздел [Выполнение операций с индексами в режиме "в сети"](../relational-databases/indexes/perform-index-operations-online.md). |
| &nbsp; | &nbsp; |

### <a name="in-memory-databases"></a>Базы данных в памяти

|Новые функции или обновления | Сведения |
|:---|:---|
|Управление DDL для гибридного буферного пула |Благодаря [гибридному буферному пулу](../database-engine/configure-windows/hybrid-buffer-pool.md) доступ к страницам базы данных, хранящимся в файлах базы данных и помещенным в устройство постоянной памяти (PMEM), осуществляется напрямую, если это необходимо.|
|Оптимизированные для памяти метаданные tempdb|См. раздел [Оптимизированные для памяти метаданные TempDB](../relational-databases/databases/tempdb-database.md#memory-optimized-tempdb-metadata)|
| &nbsp; | &nbsp; |

### <a name="linked-servers"></a>Связанные серверы

|Новые функции или обновления | Сведения |
|:---|:---|
|Связанные серверы поддерживают кодировку UTF-8. |[Поддержка параметров сортировки и Юникода](../relational-databases/collations/collation-and-unicode-support.md) |
| &nbsp; | &nbsp; |

### <a name="polybase"></a>PolyBase

|Новые функции или обновления | Сведения |
|:---|:---|
|PolyBase |Имена столбцов внешней таблицы теперь используются для запроса источников данных SQL Server, Oracle, Teradata, MongoDB и ODBC. |
| &nbsp; | &nbsp; |

### <a name="collation"></a>Параметры сортировки

|Новые функции или обновления | Сведения |
|:---|:---|
|Поддерживается кодировка UTF-8 |Включена поддержка параметров сортировки BIN2 (`Latin1_General_100_BIN2_UTF8`). См. раздел [Поддержка параметров сортировки и Юникода](../relational-databases/collations/collation-and-unicode-support.md). |
|Выбор параметра сортировки UTF-8 по умолчанию во время настройки | См. раздел [Поддержка параметров сортировки и Юникода](../relational-databases/collations/collation-and-unicode-support.md#ctp23). |
| &nbsp; | &nbsp; |

### <a name="server-settings"></a>Параметры сервера

|Новые функции или обновления | Сведения |
|:---|:---|
|Настройка значений памяти сервера `MIN` и `MAX` при установке |Во время установки вы можете настроить значения памяти сервера. Используйте значения по умолчанию и вычисляемые рекомендуемые значения или вручную указывайте собственные значения, выбрав параметр **Рекомендуется** в разделе с [параметрами конфигурации памяти сервера](../database-engine/configure-windows/server-memory-server-configuration-options.md#setting-the-memory-options-manually).|
|Программа установки SQL Server включает параметры MAXDOP |Новые рекомендации соответствуют задокументированным рекомендациям раздела [Настройка параметра конфигурации сервера max degree of parallelism](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines).|
|Гибридный буферный пул| Это новая возможность ядра СУБД SQL Server, когда доступ к страницам базы данных, хранящимся в файлах базы данных и помещенным в устройство постоянной памяти (PMEM), осуществляется напрямую при необходимости. См. раздел [Гибридный буферный пул](../database-engine/configure-windows/hybrid-buffer-pool.md).|
| &nbsp; | &nbsp; |

### <a name="performance-monitoring"></a>Мониторинг производительности

|Новые функции или обновления | Сведения |
|:---|:---|
|Встраивание скалярных пользовательских функций |Автоматически преобразует скалярные функции, определяемые пользователем (UDF), в реляционные выражения и внедряет их в вызывающий SQL-запрос. См. раздел [Встраивание скалярных определяемых пользователем функций](../relational-databases/user-defined-functions/scalar-udf-inlining.md). |
| `sys.dm_exec_requests` — столбец `command` | Отображает `SELECT (STATMAN)`, если `SELECT` ожидает завершения синхронной операции обновления статистики, прежде чем продолжить выполнение запроса. См. раздел [`sys.dm_exec_requests`](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|
|`WAIT_ON_SYNC_STATISTICS_REFRESH` | Новый тип ожидания в динамическом административном представлении `sys.dm_os_wait_stats`. Он отображает суммарное время на уровне экземпляра, затраченное на синхронные операции обновления статистики. См. раздел [`sys.dm_os_wait_stats`](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|
|Пользовательская политика записи для хранилища запросов|Если этот параметр включен, для нового параметра политики записи хранилища запросов доступны дополнительные конфигурации хранилища запросов, что позволяет тонко настраивать сбор данных на конкретном сервере. Дополнительные сведения см. в описании [параметров ALTER DATABASE SET](../t-sql/statements/alter-database-transact-sql-set-options.md).|
|`sys.dm_exec_query_plan_stats` |Новая функция динамического управления возвращает эквивалент последнего известного действительного плана выполнения для большинства запросов. См. раздел [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md).|
|`LAST_QUERY_PLAN_STATS` | Новая конфигурация области базы данных для включения `sys.dm_exec_query_plan_stats`. В разделе [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|
|`LIGHTWEIGHT_QUERY_PROFILING`|Новая конфигурация области базы данных. См. раздел [`LIGHTWEIGHT_QUERY_PROFILING`](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#lqp). |
|`query_post_execution_plan_profile` | Расширенное событие служит для сбора эквивалента действительного плана выполнения на основе упрощенного, а не стандартного профилирования, как в случае с событием `query_post_execution_showplan`. См. раздел [Инфраструктура профилирования запросов](../relational-databases/performance/query-profiling-infrastructure.md).|
|Обратная связь по временно предоставляемому буферу памяти в строковом режиме. |[Обратная связь по временно предоставляемому буферу памяти в строковом режиме](../relational-databases/performance/intelligent-query-processing.md#row-mode-memory-grant-feedback) |
|Отложенная компиляция табличных переменных.|[Отложенная компиляция табличных переменных](../relational-databases/performance/intelligent-query-processing.md#table-variable-deferred-compilation) |
|Приблизительные значения `COUNT DISTINCT`.|[Приблизительная обработка запросов](../relational-databases/performance/intelligent-query-processing.md#approximate-query-processing)|
|Пакетный режим для данных rowstore.|[Пакетный режим для данных rowstore](../relational-databases/performance/intelligent-query-processing.md#batch-mode-on-rowstore) |

### <a name="language-extensions"></a>Расширения языка

|Новые функции или обновления | Сведения |
|:---|:---|
|Новый SDK для языка Java | Упрощает разработку приложений Java, которые могут выполняться из SQL Server. См. раздел [Новые возможности служб машинного обучения SQL Server](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md). |
|Расширения языка SQL-Server — [расширение языка Java](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview)|[Пакет Microsoft SDK расширяемости для Java для Microsoft SQL Server](https://docs.microsoft.com/sql/language-extensions/how-to/extensibility-sdk-java-sql-server) теперь имеет открытый код и доступен [на GitHub](https://github.com/microsoft/sql-server-language-extensions).|
|Регистрация внешних языков|Новый DDL `CREATE EXTERNAL LANGUAGE` регистрирует внешние языки, такие как Java, в SQL Server. См. раздел [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md). |
|Поддержка типов данных Java|См. раздел [Типы данных Java](../language-extensions/how-to/java-to-sql-data-types.md).|

### <a name="spatial"></a>Пространственный

|Новые функции или обновления | Сведения |
|:---|:---|
| Новые идентификаторы пространственных ссылок (SRID) |[Australian GDA2020](http://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/datums-projections/gda2020) предоставляет более надежный и точный элемент данных, который в большей степени подходит для глобальных навигационных систем. Ниже приведены новые идентификаторы SRID:<br/><br/> — 7843 — географические двумерные;<br/> — 7844 — географические трехмерные. <br/><br/>Представление [sys.spatial_reference_systems](../relational-databases/system-catalog-views/sys-spatial-reference-systems-transact-sql.md) содержит определения новых SRID. |
| &nbsp; | &nbsp; |

### <a name="performance"></a>Производительность

|Новые функции или обновления | Сведения |
|:---|:---|
|Ускоренное восстановление баз данных. | Ускорение восстановления базы данных (ADR) для отдельных баз данных. См. раздел [Ускоренное восстановление баз данных](../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#adr).|
|Форсированная поддержка быстрых однопроходных и статических курсоров | План Query Store форсирует поддержку для перемотки вперед и статических курсоров. См. раздел [План форсирует поддержку для быстрых однопроходных и статических курсоров](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md#ctp23).|
|Сокращение повторных компиляций для рабочих нагрузок| Улучшает использование временных таблиц в нескольких областях. См. раздел [Сокращение повторных компиляций для рабочих нагрузок](../relational-databases/tables/tables.md#ctp23). |
|Масштабируемость косвенных контрольных точек |См. раздел [Улучшена масштабируемость косвенных контрольных точек](../relational-databases/logs/database-checkpoints-sql-server.md#ctp23).|
| &nbsp; | &nbsp; |

### <a name="availability-groups"></a>Группы доступности

|Новые функции или обновления | Сведения |
|:---|:---|
|До пяти синхронных реплик|В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] максимальное количество синхронных реплик увеличено до пяти, по сравнению с тремя в [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Вы можете настроить эту группу из пяти реплик для автоматического перехода на другой ресурс в пределах группы. Предоставляется одна первичная реплика и четыре синхронные вторичные реплики.|
|Перенаправление подключения от вторичной реплики к первичной| Позволяет направлять подключения клиентских приложений к первичной реплике независимо от целевого сервера, указанного в строке подключения. Дополнительные сведения см. в статье [Перенаправление подключения с правами на чтение и запись с вторичной на первичную реплику (группы доступности AlwaysOn)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md).|
| &nbsp; | &nbsp; |

### <a name="error-messages"></a>Сообщения об ошибках

|Новые функции или обновления | Сведения |
|:---|:---|
|Подробные предупреждения об усечении | Сообщение об ошибке усечения по умолчанию включает имена таблицы и столбца, а также усеченное значение. См. раздел [VERBOSE_TRUNCATION_WARNINGS](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#verbose-truncation).|
| &nbsp; | &nbsp; |

## <a name="sql-server-on-linux"></a>SQL Server в Linux

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Новый реестр контейнеров.|[Начало работы с контейнерами SQL Server в Docker](../linux/quickstart-install-connect-docker.md) |
|Группа доступности AlwaysOn в контейнерах Docker с Kubernetes. |[Группы доступности AlwaysOn для контейнеров](../linux/sql-server-ag-kubernetes.md) |
|Поддержка репликации. |[Репликация SQL Server в Linux](../linux/sql-server-linux-replication.md)
|Поддержка координатора распределенных транзакций Майкрософт (MSDTC). |[Настройка MSDTC на платформе Linux](../linux/sql-server-linux-configure-msdtc.md) |
|Поддержка OpenLDAP для сторонних поставщиков Active Directory. |[Учебник. Использование проверки подлинности Azure Active Directory с SQL Server на Linux](../linux/sql-server-linux-active-directory-authentication.md) |
|Поддержка машинного обучения в Linux. |[Настройка машинного обучения в Linux](../linux/sql-server-linux-setup-machine-learning.md) |
|Улучшения tempdb | По умолчанию новая установка SQL Server в Linux создает несколько файлов данных tempdb на основе числа логических ядер (до 8 файлов данных). Это не применимо к обновлениям основной или дополнительной версии на месте. Размер каждого файла tempdb составляет 8 МБ с возможностью автоматического увеличения до 64 МБ. Это поведение аналогично поведению установки SQL Server по умолчанию в Windows. |
| PolyBase на компьютерах под управлением Linux | [Установка PolyBase](../relational-databases/polybase/polybase-linux-setup.md) в Linux для соединителей вне Hadoop.<br/><br/>[Сопоставление типов PolyBase](../relational-databases/polybase/polybase-type-mapping.md). |
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

## <a name="analysis-services"></a>Службы Analysis Services

| Новые функции или обновления | Сведения |
|:---|:---|
|Группы вычисления в табличных моделях| [Группы вычисления в табличных моделях](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24) |
|Поддержка запросов многомерных выражений для табличных моделей с использованием групп вычислений | См. раздел [Группы вычисления](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24). |
|Динамическое форматирование мер с помощью групп вычислений |Эта функция позволяет условно изменять строки формата для мер с помощью [групп вычислений](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24). Например, благодаря преобразованию валюты меры можно отобразить с использованием разных форматов иностранных валют.|
|Связи "многие ко многим" в табличных моделях|[Связи "многие ко многим" в табличных моделях](what-s-new-in-sql-server-ver15-prerelease.md#many-to-many-ctp24)|
|Настройка свойств для регуляции ресурсов|[Настройка свойств для регуляции ресурсов](what-s-new-in-sql-server-ver15-prerelease.md#property-ctp24)|
| &nbsp; | &nbsp; |

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

Описание конкретных функций, исключенных из программы поддержки, см. в [заметках о выпуске](sql-server-ver15-release-notes.md).

Кроме того, в версии [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 3.2 добавлены или улучшены следующие функции.

## <a name="see-also"></a>См. также раздел

- [`SqlServer` Модуль PowerShell](https://www.powershellgallery.com/packages/Sqlserver)
- [Документация по SQL Server PowerShell](../powershell/sql-server-powershell.md)

## <a name="next-steps"></a>Следующие шаги

- [Заметки о выпуске [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](sql-server-ver15-release-notes.md).

- [Майкрософт [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]: Технический документ](http://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Опубликовано в сентябре 2018 г. Применяется к CTP-версии 2.0 Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] для контейнеров Windows, Linux и Docker.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
