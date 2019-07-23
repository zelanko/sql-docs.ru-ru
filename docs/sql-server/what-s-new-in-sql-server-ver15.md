---
title: Новые возможности в SQL Server 2019 | Документация Майкрософт
ms.date: 06/26/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b5c44145644b2846a2450a4da25a9e06b0f1f43c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67984707"
---
# <a name="whats-new-in-includesql-server-2019includessssqlv15-mdmd"></a>Новые возможности [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] основывается на предыдущих выпусках для расширения SQL Server как платформы, которая поддерживает ряд языков разработки, типов данных, операционных систем, а также работает в локальной и облачной средах. В этой статье перечислены новые возможности [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Статья описывает характеристики в каждом выпуске и указывает на более подробные сведения о каждой функции. Раздел [Сведения](#details) содержит технические сведения о функциях, которые могут быть недоступны в основной документации. В остальных разделах статьи приводятся сведения обо всех возможностях, выпущенных на данный момент в этой [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Дополнительные сведения и известные проблемы см. в статье с [заметками о выпуске предварительной версии [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](sql-server-ver15-release-notes.md).

**Используйте [новейшие средства](#tools) для оптимальной работы с [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].**

## <a name="ctp-31-june-2019"></a>Ознакомительная версия для сообщества 3.1 (июнь 2019 г.)

Ознакомительная версия для сообщества (CTP) 3.1 — это последний общедоступный выпуск [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. Этот выпуск включает усовершенствования предыдущих выпусков CTP для исправления ошибок, повышения безопасности и оптимизации производительности.

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

Описание конкретных функций, исключенных из программы поддержки, см. в [заметках о выпуске](sql-server-ver15-release-notes.md).

Кроме того, в версии [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 3.1 добавлены или улучшены следующие функции.

### <a name="big-data-clusters"></a>Кластеры больших данных

| Новые функции или обновления | Сведения |
|:---|:---|
| Команда `mssqlctl` изменена. | Команды `mssqlctl cluster` переименованы в `mssqlctl bdc`. См. подробнее в [справочнике по `mssqlctl`](../big-data-cluster/reference-mssqlctl.md). |
|Новые команды состояния для `mssqlsctl`.|`mssqlctl` добавляет новые команды, чтобы дополнить существующие команды мониторинга. Они заменяют средства портала администрирования кластера (в этом выпуске портал не используется).|
| Пул вычислительных ресурсов Spark | Вы можете создавать дополнительные узлы для увеличения вычислительной мощности Spark без необходимости масштабировать хранилище. Кроме того, вы можете запускать узлы пула хранилища, которые не используются для Spark. Spark и хранилище используются раздельно. См. подробнее о [настройке хранилища без Spark](../big-data-cluster/deployment-custom-configuration.md#sparkstorage). |
| Соединитель MSSQL Spark | Поддержка операций чтения и записи для внешних таблиц пула данных. В предыдущих выпусках эти операции поддерживались только для таблиц главного экземпляра. См. подробнее об [операциях чтения и записи для SQL Server из Spark с помощью соединителя Spark MSSQL](../big-data-cluster/spark-mssql-connector.md). |
| Использование Машинного обучения с MLeap | [Вы можете обучать модель машинного обучения MLeap в Spark и оценивать ее в SQL Server с помощью расширения языка Java](../big-data-cluster/spark-create-machine-learning-model.md). |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Ядро СУБД

| Новые функции или обновления | Сведения |
|:---|:---|
|Индексирование зашифрованных столбцов|Вы можете индексировать столбцы, зашифрованные с помощью случайного шифрования и ключей с поддержкой анклава, чтобы повысить производительность полнофункциональных запросов (с помощью операторов `LIKE` и операторов сравнения). См. подробнее об [использовании Always Encrypted с безопасными анклавами](../relational-databases/security/encryption/always-encrypted-enclaves.md).
|Настройка значений памяти сервера `MIN` и `MAX` при установке |Во время установки вы можете настроить значения памяти сервера. Используйте значения по умолчанию и вычисляемые рекомендуемые значения или вручную указывайте собственные значения, выбрав параметр **Рекомендуется** в разделе с [параметрами конфигурации памяти сервера](../database-engine/configure-windows/server-memory-server-configuration-options.md#setting-the-memory-options-manually).
|Новая функция графа: `SHORTEST_PATH` | Вы можете использовать `SHORTEST_PATH` в `MATCH` для поиска кратчайшего пути между любыми двумя узлами в графе или выполнения обходов произвольной длины.|
|Использование таблиц разделов и индексов для графовых баз данных|Данные секционированных таблиц и индексов разделены на блоки, которые могут распределяться между несколькими файловыми группами в графовой базе данных. |
|Новый параметр для индексов: `OPTIMIZE_FOR_SEQUENTIAL_KEY`|Включение оптимизации в ядре СУБД, что позволяет повысить пропускную способность для операций вставки с высокой степенью параллелизма в индекс. Этот параметр предназначен для индексов с состоянием состязания, возникающим при операциях вставки последней страницы (это характерно для индексов с последовательным ключом, включая столбец идентификаторов, последовательность или столбец даты и времени). См. подробнее о [CREATE INDEX](../t-sql/statements/create-index-transact-sql.md#sequential-keys).|
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>SQL Server в Linux

| Новые функции или обновления | Сведения |
|:-----|:-----|
| Улучшения tempdb | По умолчанию новая установка SQL Server в Linux создает несколько файлов данных tempdb на основе числа логических ядер (до 8 файлов данных). Это не применимо к обновлениям основной или дополнительной версии на месте. Размер каждого файла tempdb составляет 8 МБ с возможностью автоматического увеличения до 64 МБ. Это поведение аналогично поведению установки SQL Server по умолчанию в Windows. |
| &nbsp; | &nbsp; |

## <a name="ctp-30-may-2019"></a>CTP 3.0, май 2019 г.

### <a name="big-data-clusters"></a>Кластеры больших данных

| Новые функции или обновления | Сведения |
|:---|:---|
| Обновления **mssqlctl** | Несколько [обновлений команд и параметров](../big-data-cluster/reference-mssqlctl.md) **mssqlctl**. Сюда входит обновление команды **mssqlctl login**, которая теперь использует имя пользователя и конечную точку контроллера. |
| Усовершенствования хранилища | Поддержка разных конфигураций хранилища для журналов и данных. Кроме того, было уменьшено количество утверждений постоянного тома для больших кластеров данных. |
| Несколько экземпляров вычислительного пула | Поддержка нескольких экземпляров вычислительного пула. |
| Новые возможности и поведение пулов | Теперь вычислительный пул используется по умолчанию для операций с пулом носителей и пулом данных только при распределении **ROUND_ROBIN**. Пул данных теперь может использовать новый тип распределения **REPLICATED**, то есть одни и те же данные присутствуют во всех экземплярах пула данных. |
| Усовершенствования внешних таблиц | Внешние таблицы, имеющие тип источника данных HADOOP, теперь поддерживают чтение строк размером до 1 МБ. Внешние таблицы (ODBC, пул носителей, пул данных) теперь поддерживают строки шириной с таблицу SQL Server. |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Ядро СУБД

| Новые функции или обновления | Сведения |
|:---|:---|
|Расширения языка SQL-Server — [расширение языка Java](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview)|[Пакет Microsoft SDK расширяемости для Java для Microsoft SQL Server](https://docs.microsoft.com/sql/language-extensions/how-to/extensibility-sdk-java-sql-server) теперь имеет открытый код и доступен [на GitHub](https://github.com/microsoft/sql-server-language-extensions).|
|Регистрация внешних языков|Новый DDL `CREATE EXTERNAL LANGUAGE` регистрирует внешние языки, такие как Java, в SQL Server. См. раздел [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md). |
|Дополнительные поддерживаемые типы данных для Java|См. раздел [Типы данных Java](../language-extensions/how-to/java-to-sql-data-types.md).|
|Пользовательская политика записи для хранилища запросов|Если этот параметр включен, для нового параметра политики записи хранилища запросов доступны дополнительные конфигурации хранилища запросов, что позволяет тонко настраивать сбор данных на конкретном сервере. Дополнительные сведения см. в описании [параметров ALTER DATABASE SET](../t-sql/statements/alter-database-transact-sql-set-options.md).|
|[Выполняющаяся в памяти база данных](../relational-databases/in-memory-database.md) добавляет новый синтаксис DDL для управления гибридным буферным пулом. <sup>2</sup>|Благодаря [гибридному буферному пулу](../database-engine/configure-windows/hybrid-buffer-pool.md) доступ к страницам базы данных, хранящимся в файлах базы данных и помещенным в устройство постоянной памяти (PMEM), осуществляется напрямую, если это необходимо.|
|Добавлена новая функция выполняющейся в памяти базы данных — оптимизированные для памяти метаданные tempdb.|См. раздел [Оптимизированные для памяти метаданные TempDB](../relational-databases/databases/tempdb-database.md#memory-optimized-tempdb-metadata)|
|Связанные серверы поддерживают кодировку UTF-8. |[Поддержка параметров сортировки и Юникода](../relational-databases/collations/collation-and-unicode-support.md) |
|Имя параметров сортировки BIN2_UTF8 изменено на Latin1_General_100_BIN2_UTF8. |[Поддержка параметров сортировки и Юникода](../relational-databases/collations/collation-and-unicode-support.md) |
|Программа установки SQL Server включает в себя рекомендации MaxDOP, которые следуют указаниям в документации. |[Настройка параметра конфигурации сервера max degree of parallelism](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines)|
|`sys.dm_exec_query_plan_stats` возвращает дополнительные сведения о степени параллелизма и временно предоставляемых буферах памяти для планов запросов. |[sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
| &nbsp; | &nbsp; |

><sup>1</sup> Эта функция активируется явным образом и требует включения [флага трассировки](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451.
>
><sup>2</sup> Флаг трассировки больше не требуется для включения гибридного буферного пула.

### [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]

| Новые функции или обновления | Сведения |
|:---|:---|
|[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] поддерживает базы данных Управляемого экземпляра базы данных SQL Azure.| Размещение [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] на управляемом экземпляре. См. раздел [Установка и настройка [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]](../master-data-services/master-data-services-installation-and-configuration.md#SetUpWeb).
| &nbsp; | &nbsp; |

### <a name="analysis-services"></a>Службы Analysis Services

| Новые функции или обновления | Сведения |
|:---|:---|
|Поддержка запросов многомерных выражений для табличных моделей с использованием групп вычислений. |В этом выпуске убрано действовавшее ранее ограничение для [групп вычислений](#calc-ctp24). |
|Динамическое форматирование мер с помощью групп вычислений. |Эта функция позволяет условно изменять строки формата для мер с помощью [групп вычислений](#calc-ctp24). Например, благодаря преобразованию валюты меры можно отобразить с использованием разных форматов иностранных валют.|
| &nbsp; | &nbsp; |

## <a name="ctp-25-april-2019"></a>CTP-версия 2.5, апрель 2019 г.

### <a name="big-data-clusters"></a>Кластеры больших данных

| Новые функции или обновления | Сведения |
|:---|:---|
| Профили развертывания | Используйте стандартные и настраиваемые [JSON-файлы конфигурации развертывания](../big-data-cluster/deployment-guidance.md#configfile) для развертывания кластера больших данных вместо переменных среды. |
| Развертывания с подсказками | `mssqlctl cluster create` теперь запрашивает все необходимые параметры для развертывания по умолчанию. |
| Изменение имен конечной точки службы и pod | Дополнительные сведения см. в [Заметках о выпуске кластера больших данных](../big-data-cluster/release-notes-big-data-cluster.md). |
| Улучшения **mssqlctl** | Используйте **mssqlctl** для [перечисления внешних конечных точек](../big-data-cluster/deployment-guidance.md#endpoints) и проверяйте версию **mssqlctl** с помощью параметра `--version`. |
| Автономная установка | [Руководство для развертывания автономного кластера больших данных](../big-data-cluster/deploy-offline.md). |
| Усовершенствования распределения по уровням HDFS | HDFS, распределение по уровням в службе хранилища Amazon S3. Поддержка OAuth для ADLS 2-го поколения. Функции кэширования для повышения производительности. Дополнительные сведения см. в разделе [Распределение по уровням HDFS](../big-data-cluster/hdfs-tiering.md). |
| Соединитель Spark и SQL Server | [Чтение и запись в SQL Server из Spark с помощью соединителя JDBC MSSQL](../big-data-cluster/spark-mssql-connector.md) |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Ядро СУБД

| Новые функции или обновления | Сведения |
|:---|:---|
| PolyBase на компьютерах под управлением Linux. | [Установка PolyBase](../relational-databases/polybase/polybase-linux-setup.md) в Linux для соединителей вне Hadoop.<br/><br/>[Сопоставление типов PolyBase](../relational-databases/polybase/polybase-type-mapping.md). |
| Новый пакет Java SDK для SQL Server. | Упрощает разработку приложений Java, которые могут выполняться из SQL Server. См. раздел [Новые возможности служб машинного обучения SQL Server](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md). |
| Расширена область планов, доступных в DMF `sys.dm_exec_query_plan_stats`. |См. раздел [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
| Новая конфигурация области базы данных `LAST_QUERY_PLAN_STATS` для включения `sys.dm_exec_query_plan_stats`. |См. раздел [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|
| Новые идентификаторы пространственных ссылок (SRID). |[Australian GDA2020](http://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/datums-projections/gda2020) предоставляет более надежный и точный элемент данных, который в большей степени подходит для глобальных навигационных систем. Ниже приведены новые идентификаторы SRID:<br/><br/> — 7843 — географические двумерные;<br/> — 7844 — географические трехмерные. <br/><br/>Представление [sys.spatial_reference_systems](../relational-databases/system-catalog-views/sys-spatial-reference-systems-transact-sql.md) содержит определения новых SRID. |
| &nbsp; | &nbsp; |

><sup>1</sup> Это дополнительная функция, требующая включения [флага трассировки](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 или параметра `LAST_QUERY_PLAN_STATS` в конфигурации уровня базы данных.

## <a name="ctp-24-march-2019"></a>CTP-версия 2.4, март 2019 г.

### <a name="big-data-clusters"></a>Кластеры больших данных

| Новые функции или обновления | Сведения |
|:---|:---|
| Руководство по использованию GPU для выполнения глубокого обучения с помощью библиотеки TensorFlow в Spark. | [Развертывание кластера больших данных с поддержкой GPU и запуск TensorFlow](../big-data-cluster/spark-gpu-tensorflow.md). |
| Источники данных **SqlDataPool** и **SqlStoragePool** больше не создаются по умолчанию. | Создайте их вручную при необходимости. Ознакомьтесь с [известными проблемами](../big-data-cluster/release-notes-big-data-cluster.md#externaltablesctp24). |
| Поддержка `INSERT INTO SELECT` для пула данных. | Пример см. в разделе [Учебник. Прием данных в пул данных SQL Server с помощью Transact-SQL](../big-data-cluster/tutorial-data-pool-ingest-sql.md). |
| Параметры `FORCE SCALEOUTEXECUTION` и `DISABLE SCALEOUTEXECUTION`. | См. [Заметки о выпуске кластера больших данных](../big-data-cluster/release-notes-big-data-cluster.md#whats-new).|
| Обновленные рекомендации по развертыванию AKS. | При анализе кластеров больших данных в AKS теперь рекомендуется использовать один узел размера **Standard_L8s**. |
| Обновление среды выполнения Spark до версии Spark 2.4. | |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Ядро СУБД

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Сообщение об ошибке усечения по умолчанию включает имена таблицы и столбца, а также усеченное значение.|[VERBOSE_TRUNCATION_WARNINGS](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#verbose-truncation)|
|Новая функция динамического управления `sys.dm_exec_query_plan_stats` возвращает эквивалент последнего известного действительного плана выполнения для большинства запросов. |[sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
|Новое расширенное событие `query_post_execution_plan_profile` служит для сбора эквивалента действительного плана выполнения на основе упрощенного, а не стандартного профилирования, как в случае с событием `query_post_execution_showplan`. |[Инфраструктура профилирования запросов](../relational-databases/performance/query-profiling-infrastructure.md)|
|Приостановка и возобновление сканирования прозрачного шифрования данных (TDE).|[Приостановка и возобновление сканирования прозрачного шифрования данных (TDE)](../relational-databases/security/encryption/transparent-data-encryption.md#scan-suspend-resume)|
| &nbsp; | &nbsp; |

><sup>1</sup> Эта функция активируется явным образом и требует включения [флага трассировки](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451.

### <a name="sql-server-analysis-services-ssas"></a>Службы SQL Server Analysis Services (SSAS)

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Связи "многие ко многим" в табличных моделях.|[Связи "многие ко многим" в табличных моделях](#many-to-many-ctp24)|
|Настройка свойств для регуляции ресурсов.|[Настройка свойств для регуляции ресурсов](#property-ctp24)|
| &nbsp; | &nbsp; |

## <a name="ctp-23-february-2019"></a>CTP-версия 2.3, февраль 2019 г.

### <a name="big-data-clusters"></a>Кластеры больших данных

| Новые функции или обновления | Сведения |
| :---------- | :------ |
| Отправка заданий Spark в кластерах больших данных в IntelliJ. | [Отправка заданий Spark в кластерах больших данных SQL Server 2019 в IntelliJ](../big-data-cluster/spark-submit-job-intellij-tool-plugin.md) |
| Общий интерфейс командной строки для развертывания приложений и управления кластерами. | [Развертывание приложения в кластере больших данных SQL Server 2019 (предварительная версия)](../big-data-cluster/big-data-cluster-create-apps.md) |
| Расширение VS Code для развертывания приложений в кластере больших данных. | [Как использовать VS Code для развертывания приложений в кластерах больших данных SQL Server](../big-data-cluster/app-deployment-extension.md) |
| Изменения в использовании команды **mssqlctl**. | Дополнительные сведения см. в разделе [Известные проблемы mssqlctl](../big-data-cluster/release-notes-big-data-cluster.md#mssqlctlctp23). |
| Использование Sparklyr в кластерах больших данных. | [Использование Sparklyr в кластерах больших данных SQL Server 2019](../big-data-cluster/sparklyr-from-RStudio.md) |
| Подключение внешнего HDFS-совместимого хранилища к кластеру больших данных с **распределением HDFS по уровням**. | См. раздел [Распределение по уровням HDFS](../big-data-cluster/hdfs-tiering.md). |
| Новые возможности единого подключения для главного экземпляра SQ Server и шлюза HDFS или Spark. | См. раздел [Главный экземпляр SQL Server и шлюз HDFS или Spark](../big-data-cluster/connect-to-big-data-cluster.md). |
| При удалении кластера с помощью команды **mssqlctl cluster delete** теперь удаляются только объекты в пространстве имен, которые были частью кластера больших данных. | Пространство имен не удаляется. Однако в более ранних выпусках эта команда удаляла все пространство имен. |
| Имена конечных точек _безопасности_ были изменены и консолидированы. | Точки **service-security-lb** и **service-security-nodeport** были объединены в конечной точке **endpoint-security**. |
| Имена конечных точек _прокси_ были изменены и консолидированы. | Точки **service-proxy-lb** и **service-proxy-nodeport** были объединены в конечной точке **endpoint-service-proxy**. |
| Имена конечных точек _контроллера_ были изменены и консолидированы. | Точки **service-mssql-controller-lb** и **service-mssql-controller-nodeport** были объединены в конечную точку **endpoint-controller**. |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Ядро СУБД

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Ускорение восстановления базы данных может быть включено для отдельных баз данных.| [Ускоренное восстановление баз данных](../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#adr)|
|План Query Store форсирует поддержку для перемотки вперед и статических курсоров.|[План форсирует поддержку для перемотки вперед и статических курсоров](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md#ctp23) |
|Сокращение повторных компиляций для рабочих нагрузок с использованием темпоральных таблиц в нескольких областях. |[Сокращение повторных компиляций для рабочих нагрузок](../relational-databases/tables/tables.md#ctp23) |
|Улучшена масштабируемость косвенных контрольных точек. |[Улучшена масштабируемость косвенных контрольных точек](../relational-databases/logs/database-checkpoints-sql-server.md#ctp23)|
|Добавлена поддержка использования кодировки UTF-8 с параметрами сортировки BIN2 (`UTF8_BIN2`). |[Поддержка параметров сортировки и Юникода](../relational-databases/collations/collation-and-unicode-support.md) |
|Определение каскадных действий удаления для ограничения ребер в базе данных графов. |[Ограничения ребер](../relational-databases/tables/graph-edge-constraints.md) |
|Включение или отключение `LIGHTWEIGHT_QUERY_PROFILING` с учетом новой конфигурации уровня базы данных. |[`LIGHTWEIGHT_QUERY_PROFILING`](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#lqp) |
| &nbsp; | &nbsp; |

### <a name="tools"></a>Инструменты

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Azure Data Studio поддерживает Azure Active Directory. |[Azure Data Studio](../azure-data-studio/what-is.md) |
|Представление пользовательского интерфейса записной книжки было перемещено в ядро Azure Data Studio. |[Как управлять записными книжками в Azure Data Studio](../big-data-cluster/notebooks-how-to-manage.md) |
|Добавлен новый мастер создания внешних источников данных из распределенной файловой системы Hadoop (HDFS) в кластере больших данных SQL Server. | [Инструменты](#tools-ctp23)|
|Улучшен пользовательский интерфейс средства просмотра записной книжки. | [Инструменты](#tools-ctp23) |
|Добавлены новые интерфейсы API записной книжки.| [Инструменты](#tools-ctp23) |
|Добавлена команда "Переустановить зависимости записной книжки" с обновлениями пакета Python. | [Инструменты](#tools-ctp23) |
|Запустить Azure Data Studio можно из SSMS.| [Инструменты](#tools-ctp23) |
| &nbsp; | &nbsp; |

### <a name="analysis-services"></a>Службы Analysis Services

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Группы вычисления в табличных моделях.| [Группы вычисления в табличных моделях](#calc-ctp24) |
| &nbsp; | &nbsp; |

## <a name="ctp-22-december-2018"></a>CTP-версия 2.2, декабрь 2018 г.

### <a name="big-data-clusters"></a>Кластеры больших данных

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Использование SparkR из Azure Data Studio в кластерах больших данных. | |
|Развертывание приложений Python и R.|[Развертывание приложений с помощью mssqlctl](../big-data-cluster/big-data-cluster-create-apps.md) |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Ядро СУБД

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Добавлена поддержка использования кодировки UTF-8 с репликацией SQL Server. |[Поддержка параметров сортировки и Юникода](../relational-databases/collations/collation-and-unicode-support.md#ctp23) |
| &nbsp; | &nbsp; |


### <a name="sql-server-on-linux"></a>SQL Server в Linux

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Группа доступности AlwaysOn в контейнерах Docker с Kubernetes. |[Группы доступности AlwaysOn для контейнеров](../linux/sql-server-ag-kubernetes.md) |
| &nbsp; | &nbsp; |

## <a name="ctp-21-november-2018"></a>CTP-версия 2.1, ноябрь 2018 г.

### <a name="database-engine"></a>Ядро СУБД

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Добавлена возможность выбора параметров сортировки UTF-8 по умолчанию во время настройки [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. |[Поддержка параметров сортировки и Юникода](../relational-databases/collations/collation-and-unicode-support.md#ctp23) |
|Функция масштабируемого встраивания определяемых пользователем функций автоматически преобразует скалярные функции, определяемые пользователем (UDF), в реляционные выражения и внедряет их в вызывающий SQL-запрос. |[Встраивание скалярных определяемых пользователем функций](../relational-databases/user-defined-functions/scalar-udf-inlining.md) |
|В динамическом административном представлении `sys.dm_exec_requests` столбец `command` отображает `SELECT (STATMAN)`, если `SELECT` ожидает завершения синхронной операции обновления статистики, прежде чем продолжить выполнение запроса. | [`sys.dm_exec_requests`](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) |
|Отображается новый тип ожидания `WAIT_ON_SYNC_STATISTICS_REFRESH` в динамическом административном представлении `sys.dm_os_wait_stats`. Он отображает суммарное время на уровне экземпляра, затраченное на синхронные операции обновления статистики.|[`sys.dm_os_wait_stats`](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md) |
|Гибридный буферный пул — это новая возможность ядра СУБД SQL Server, когда доступ к страницам базы данных, хранящимся в файлах базы данных и помещенным в устройство постоянной памяти (PMEM), осуществляется напрямую при необходимости.|[Гибридный буферный пул](../database-engine/configure-windows/hybrid-buffer-pool.md) |
|Использование псевдонимов производной таблицы или представления для графовых запросов MATCH |[Ограничения ребер графа](../relational-databases/tables/graph-edge-constraints.md) |
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>SQL Server в Linux

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Новый реестр контейнеров для SQL Server. |[Начало работы с контейнерами SQL Server в Docker](../linux/quickstart-install-connect-docker.md) |
| &nbsp; | &nbsp; |

### <a name="tools"></a>Инструменты

| Новые функции или обновления | Сведения |
|:-----|:-----|
|[Azure Data Studio](../azure-data-studio/what-is.md) поддерживает подключение и управление кластерами больших данных [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. | |
| &nbsp; | &nbsp; |

## <a name="ctp-20-october-2018"></a>CTP-версия 2.0, октябрь 2018 г.

### <a name="big-data-clusters"></a>Кластеры больших данных

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Развертывание кластера больших данных с использованием контейнеров Linux Spark и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Kubernetes. | |
|Доступ к большим данным из HDFS. | |
|Выполнение функций расширенной аналитики и машинного обучения с помощью Spark. | |
|Использование потоковой передачи данных Spark в пулы данных SQL. | |
|Запуск книг запросов, обеспечивающих условия работы с записной книжкой в **Azure Data Studio**.|[Проектирование данных](../azure-data-studio/what-is.md#data-engineering)|
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Ядро СУБД

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Добавлен **уровень совместимости 150** для базы данных. |[Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) |
|Возобновляемое создание индексов в подключенном режиме.|[Инструкция CREATE INDEX (Transact-SQL)](../t-sql/statements/create-index-transact-sql.md#resumable-indexes) |
|Обратная связь по временно предоставляемому буферу памяти в строковом режиме. |[Обратная связь по временно предоставляемому буферу памяти в строковом режиме](../relational-databases/performance/intelligent-query-processing.md#row-mode-memory-grant-feedback) |
|Приблизительные значения `COUNT DISTINCT`.|[Приблизительная обработка запросов](../relational-databases/performance/intelligent-query-processing.md#approximate-query-processing)|
|Пакетный режим для данных rowstore.|[Пакетный режим для данных rowstore](../relational-databases/performance/intelligent-query-processing.md#batch-mode-on-rowstore) |
|Отложенная компиляция табличных переменных.|[Отложенная компиляция табличных переменных](../relational-databases/performance/intelligent-query-processing.md#table-variable-deferred-compilation) |
|Расширение языка Java.|[Расширение языка Java](../advanced-analytics/java/extension-java.md) |
|Объедините текущие данные графа из таблиц узлов или ребер с новыми данными с помощью предикатов `MATCH` в инструкции `MERGE`. | |
|Ограничения ребер.|[Ограничения ребер графа](../relational-databases/tables/graph-edge-constraints.md) |
|Параметр по умолчанию на уровне базы данных для возобновляемых операций DDL и операций DDL в подключенном режиме.| |
|Группы доступности поддерживают до пяти синхронных вторичных реплик.|[Группы доступности](../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) |
|Перенаправление подключения с правами на чтение и запись с вторичной на первичную реплику|[Перенаправление подключения с правами на чтение и запись с вторичной на первичную реплику (группы доступности Always On)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md) |
|Обнаружение и классификация данных SQL.| [Обнаружение и классификация данных SQL](../relational-databases/security/sql-data-discovery-and-classification.md) |
|Расширенная поддержка устройств с постоянной памятью.|[Гибридный буферный пул](../database-engine/configure-windows/hybrid-buffer-pool.md) |
|Поддержка статистики columnstore в `DBCC CLONEDATABASE`.|[BLOB-объект статистики для индексов columnstore](../t-sql/database-console-commands/dbcc-clonedatabase-transact-sql.md#ctp23)|
|В `sp_estimate_data_compression_savings` появились `COLUMNSTORE` и `COLUMNSTORE_ARCHIVE`.|[Рекомендации для индексов columnstore](../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md#considerations-for-columnstore-indexes)|
|Службы машинного обучения поддерживаются в отказоустойчивом кластере Windows Server. |[Новые возможности — службы машинного обучения SQL Server](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)|
|Поддержка машинного обучения для моделирования на основе секций.|[Новые возможности — службы машинного обучения SQL Server](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md) |
|Упрощенная инфраструктура профилирования запросов включена по умолчанию |[Упрощенная инфраструктура профилирования статистики выполнения запросов версии 3](../relational-databases/performance/query-profiling-infrastructure.md#lightweight-query-execution-statistics-profiling-infrastructure-v3) |
|Новые соединители PolyBase для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata и MongoDB. |[Что такое PolyBase?](../relational-databases/polybase/polybase-guide.md) |
|`sys.dm_db_page_info(database_id, file_id, page_id, mode)` возвращает сведения о странице в базе данных. |[sys.dm_db_page_info (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)|
|Always Encrypted с безопасными анклавами. |[Always Encrypted с безопасными анклавами](../relational-databases/security/encryption/always-encrypted-enclaves.md) |
|Сборка и перестройка кластеризованных индексов columnstore в подключенном режиме. |[Выполнение операции с индексами в сети](../relational-databases/indexes/perform-index-operations-online.md) |
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>SQL Server в Linux

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Поддержка репликации. |[Репликация SQL Server в Linux](../linux/sql-server-linux-replication.md)
|Поддержка координатора распределенных транзакций Майкрософт (MSDTC). |[Настройка MSDTC на платформе Linux](../linux/sql-server-linux-configure-msdtc.md) |
|Поддержка OpenLDAP для сторонних поставщиков Active Directory. |[Учебник. Использование проверки подлинности Azure Active Directory с SQL Server на Linux](../linux/sql-server-linux-active-directory-authentication.md) |
|Поддержка машинного обучения в Linux. |[Настройка машинного обучения в Linux](../linux/sql-server-linux-setup-machine-learning.md) |
| &nbsp; | &nbsp; |

### <a name="master-data-services"></a>Службы Master Data Services

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Теперь портал Master Data Services (MDS) не зависит от Silverlight.| Все прежние компоненты Silverlight заменены элементами управления HTML.|
| &nbsp; | &nbsp; |

### <a name="security"></a>безопасность

| Новые функции или обновления | Сведения |
|:-----|:-----|
|Управление сертификатами в диспетчере конфигурации SQL Server.|[Управление сертификатами (диспетчер конфигурации SQL Server)](../database-engine/configure-windows/manage-certificates.md)
| &nbsp; | &nbsp; |

### <a name="tools"></a>Инструменты

| Новые функции или обновления | Сведения |
|:-----|:-----|
|[Azure Data Studio](../azure-data-studio/what-is.md) поддерживает подключение и управление кластерами больших данных [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. |[Что такое Azure Data Studio](../azure-data-studio/what-is.md)|
|Поддержка сценариев, в которых используется кластер больших данных SQL Server. |[Расширение SQL Server 2019 (предварительная версия)](../azure-data-studio/sql-server-2019-extension.md)|
|[**SQL Server Management Studio (SSMS) 18.0 (предварительная версия)** ](../ssms/sql-server-management-studio-ssms.md): поддерживает [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].| |
|Поддержка функции Always Encrypted с безопасными анклавами. |[Always Encrypted с безопасными анклавами](../relational-databases/security/encryption/always-encrypted-enclaves.md)|
| &nbsp; | &nbsp; |


## <a name="other-services"></a>Другие службы

Начиная с версии CTP 2.4 в [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] не были добавлены новые возможности для следующих служб:

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS);
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS).

## <a name="details"></a>Сведения

### <a id="bigdatacluster"></a>Кластеры больших данных

[Кластеры больших данных](../big-data-cluster/big-data-cluster-overview.md) ([!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]) позволяют реализовать новые сценарии, включая следующие:

- [Поддержка GPU для выполнения глубокого обучения с помощью библиотеки TensorFlow в Spark](../big-data-cluster/spark-gpu-tensorflow.md). (CTP 2.4)
- Обновление среды выполнения Spark до версии Spark 2.4. (CTP 2.4)
- `INSERT INTO SELECT` поддерживается для пула данных (CTP 2.4).
- Предложения OPTION `FORCE SCALEOUTEXECUTION` и `DISABLE SCALEOUTEXECUTION` для запросов к внешним таблицам. (CTP 2.4)
- [Отправка заданий Spark в кластерах больших данных [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] в IntelliJ](../big-data-cluster/spark-submit-job-intellij-tool-plugin.md). (CTP-версия 2.3)
- [Интерфейс управления и развертывания для различных приложений](../big-data-cluster/big-data-cluster-create-apps.md), связанных с данными, включая эксплуатацию моделей машинного обучения с помощью R и Python, запуск заданий служб SQL Server Integration Services (SSIS) и многое другое. (CTP-версия 2.3)
- [Использование Sparklyr в кластерах больших данных [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](../big-data-cluster/sparklyr-from-RStudio.md). (CTP-версия 2.3)
- Подключение внешнего HDFS-совместимого хранилища к кластеру больших данных с [распределением HDFS по уровням](../big-data-cluster/hdfs-tiering.md). (CTP-версия 2.3)
- Использование SparkR из Azure Data Studio в кластерах больших данных. (CTP 2.2)
- [Развертывание приложений Python и R](../big-data-cluster/big-data-cluster-create-apps.md). (CTP 2.2)
- Развертывание кластера больших данных с использованием контейнеров Linux Spark и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Kubernetes. (CTP 2.0)
- Доступ к большим данным из HDFS. (CTP 2.0)
- Выполнение функций расширенной аналитики и машинного обучения с помощью Spark. (CTP 2.0)
- Использование потоковой передачи данных Spark в пулы данных SQL. (CTP 2.0)
- Запуск книг запросов, обеспечивающих условия работы с записной книжкой в [**Azure Data Studio**](../sql-operations-studio/what-is.md). (CTP 2.0)
 
[!INCLUDE [Big data clusters preview](../includes/big-data-cluster-preview-note.md)]

### <a id="databaseengine"></a> Ядро СУБД

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] обеспечивает реализацию или оптимизацию перечисленных ниже новых функций для [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].

#### <a name="new-querypostexecutionplanprofile-extended-event-ctp-24"></a>Новое расширенное событие query_post_execution_plan_profile (CTP 2.4)

Новое расширенное событие `query_post_execution_plan_profile` служит для сбора эквивалента действительного плана выполнения на основе упрощенного, а не стандартного профилирования, как в случае с событием `query_post_execution_showplan`. Дополнительные сведения см. в статье [Инфраструктура профилирования запросов](../relational-databases/performance/query-profiling-infrastructure.md).

##### <a name="example-1---extended-event-session-using-standard-profiling"></a>Пример 1. Сеанс расширенных событий на основе стандартного профилирования

```sql
CREATE EVENT SESSION [QueryPlanOld] ON SERVER 
ADD EVENT sqlserver.query_post_execution_showplan(
    ACTION(sqlos.task_time, sqlserver.database_id, 
    sqlserver.database_name, sqlserver.query_hash_signed, 
    sqlserver.query_plan_hash_signed, sqlserver.sql_text))
ADD TARGET package0.event_file(SET filename = N'C:\Temp\QueryPlanStd.xel')
WITH (MAX_MEMORY=4096 KB, EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS, 
    MAX_DISPATCH_LATENCY=30 SECONDS, MAX_EVENT_SIZE=0 KB, 
    MEMORY_PARTITION_MODE=NONE, TRACK_CAUSALITY=OFF, STARTUP_STATE=OFF);
```

##### <a name="example-2---extended-event-session-using-lightweight-profiling"></a>Пример 2. Сеанс расширенных событий на основе упрощенного профилирования

```sql
CREATE EVENT SESSION [QueryPlanLWP] ON SERVER 
ADD EVENT sqlserver.query_post_execution_plan_profile(
    ACTION(sqlos.task_time, sqlserver.database_id, 
    sqlserver.database_name, sqlserver.query_hash_signed, 
    sqlserver.query_plan_hash_signed, sqlserver.sql_text))
ADD TARGET package0.event_file(SET filename=N'C:\Temp\QueryPlanLWP.xel')
WITH (MAX_MEMORY=4096 KB, EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS, 
    MAX_DISPATCH_LATENCY=30 SECONDS, MAX_EVENT_SIZE=0 KB, 
    MEMORY_PARTITION_MODE=NONE, TRACK_CAUSALITY=OFF, STARTUP_STATE=OFF);
```

#### <a name="new-dmf-sysdmexecqueryplanstats-ctp-24"></a>Новая функция динамического управления sys.dm_exec_query_plan_stats (CTP 2.4) 

Новая функция динамического управления `sys.dm_exec_query_plan_stats` возвращает эквивалент последнего известного действительного плана выполнения для большинства запросов на основе упрощенного профилирования. Дополнительные сведения см. в разделах [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md) и [Инфраструктура профилирования запросов](../relational-databases/performance/query-profiling-infrastructure.md). Рассмотрите следующий сценарий в качестве примера:

```sql
SELECT *
FROM sys.dm_exec_cached_plans
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle)
WHERE objtype ='Trigger';
GO
```

Эта функция активируется явным образом и требует включения [флага трассировки](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451.

#### <a name="transparent-data-encryption-tde-scan---suspend-and-resume-ctp-24"></a>Приостановка и возобновление сканирования прозрачного шифрования данных (TDE) (CTP 2.4)

Чтобы включить [прозрачное шифрование данных (TDE)](../relational-databases/security/encryption/transparent-data-encryption.md) для базы данных, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] должен выполнить сканирование шифрования. При этом каждая страница считывается из файлов данных в буферный пул, после чего зашифрованные страницы записываются обратно на диск. Для предоставления пользователю большего контроля над сканированием шифрования в [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] появился синтаксис приостановки и возобновления сканирования TDE. Он позволяет приостанавливать сканирование, когда система сильно загружена, или в критически важные периоды времени, а затем возобновлять сканирование.

Чтобы приостановить сканирование шифрования TDE, используйте следующий синтаксис:

```sql
ALTER DATABASE <db_name> SET ENCRYPTION SUSPEND;
```

Чтобы возобновить сканирование шифрования TDE, используйте следующий синтаксис:

```sql
ALTER DATABASE <db_name> SET ENCRYPTION RESUME;
```

Для определения текущего состояния сканирования шифрования в динамическое административное представление `sys.dm_database_encryption_keys` добавлен столбец `encryption_scan_state`. Кроме того, появился столбец `encryption_scan_modify_date`, который содержит дату и время последнего изменения состояния сканирования шифрования. Кроме того, обратите внимание на то, что если экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] перезапускается, когда сканирование шифрования приостановлено, при запуске в журнал ошибок записывается сообщение о том, что имеется приостановленное сканирование.

#### <a name="accelerated-database-recovery-ctp-23"></a>Ускоренное восстановление баз данных (CTP-версия 2.3).

[Ускорение восстановления баз данных](/azure/sql-database/sql-database-accelerated-database-recovery/) значительно повышает доступность баз данных, особенно при наличии продолжительных транзакций, за счет перепроектирования процесса восстановления ядра базы данных SQL Server. [Восстановление базы данных](../relational-databases/logs/the-transaction-log-sql-server.md?#recovery-of-all-incomplete-transactions-when--is-started) — это процесс, который SQL Server использует в каждой базе данных для ее запуска в транзакционно-согласованном (чистом) состоянии. Базы данных при включении ускоренного восстановления значительно быстрее восстанавливаются после отработки отказа или других вариантов завершения работы в "грязном" состоянии. С CTP-версии 2.3 можно включить ускоренной восстановление для каждой базы данных отдельно с помощью следующего синтаксиса:

```sql
ALTER DATABASE <db_name> SET ACCELERATED_DATABASE_RECOVERY = {ON | OFF}
```

> [!NOTE]
> Этот синтаксис не требуется, чтобы воспользоваться преимуществами этой функции в БД SQL Azure, в которой она [включается по запросу на период действия общедоступной предварительной версии](/azure/sql-database/sql-database-accelerated-database-recovery). После активации функция включена по умолчанию.

При наличии важных баз данных, в которых могут происходить большие транзакции, поэкспериментируйте с этой функцией на этапе предварительной версии. Отправьте отзыв [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] разработчикам](<https://aka.ms/sqlfeedback>).

#### <a name="query-store-plan-forcing-support-for-fast-forward-and-static-cursors-ctp-23"></a>План Query Store форсирует поддержку для перемотки вперед и статических курсоров (CTP-версия 2.3).

Query Store теперь поддерживает возможность форсирования планов выполнения запросов с перемоткой вперед и статическими курсорами в T-SQL и API. Форсирование теперь поддерживается через `sp_query_store_force_plan` или с помощью отчетов SQL Server Management Studio Query Store.

#### <a name="reduced-recompilations-for-workloads-using-temporary-tables-across-multiple-scopes-ctp-23"></a>Сокращение повторных компиляций для рабочих нагрузок с использованием темпоральных таблиц в нескольких областях (CTP-версия 2.3).

До этого выпуска при ссылке на временную таблицу в инструкции на языке обработки данных DML (`SELECT`, `INSERT`, `UPDATE`, `DELETE`), если таблица была создана пакетом во внешней области, происходила повторная компиляция инструкции DML при каждом выполнении. В рамках этого улучшения SQL Server выполняет дополнительные упрощенные проверки, чтобы избежать ненужных перекомпиляций:

- Проверяет, совпадает ли модуль внешней области, использованный для создания темпоральной таблицы во время компиляции, с используемым для последующих выполнений. 
- Отслеживает все изменения языка DDL определения данных, сделанные при первичной компиляции, и сравнивает их с операциями DDL в последующих запусках. 

Конечным результатом является снижение числа лишних перекомпиляций и нагрузки на ЦП.

#### <a name="improved-indirect-checkpoint-scalability-ctp-23"></a>Улучшена масштабируемость косвенных контрольных точек (CTP-версия 2.3).

В предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] пользователи могут сталкиваться с ошибками невыполнения в планировщике при наличии базы данных, которая создает большое количество "грязных" страниц, такой как tempdb. В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] улучшена масштабируемость косвенных контрольных точек, что должно помочь избежать подобных ошибок в базах данных с высокой рабочей нагрузкой вида UPDATE или INSERT.

#### <a name="utf-8-support-ctp-23"></a>Поддержка UTF-8 (CTP 2.3)

Полная поддержка широко используемой кодировки символов UTF-8 как кодировки импорта или экспорта или как параметров сортировки на уровне столбцов и базы данных для текстовых данных. Кодировка символов UTF-8 допускается в типах данных `CHAR` и `VARCHAR`. Она активируется при создании параметров сортировки с суффиксом `UTF8` или изменении существующих параметров на такие. 

Например, `LATIN1_GENERAL_100_CI_AS_SC` меняется на `LATIN1_GENERAL_100_CI_AS_SC_UTF8`. UTF-8 доступна только для параметров сортировки Windows, которые поддерживают дополнительные символы, представленные в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]. `NCHAR` и `NVARCHAR` допускают только кодирование UTF-16 и остаются неизменными.

Эта функция может обеспечить значительную экономию места в хранилище в зависимости от используемой кодировки. Например, изменение имеющегося типа данных столбца со строками в кодировке ASCII (латинская) с `NCHAR(10)` на `CHAR(10)` с использованием параметров сортировки для UTF-8 на 50 % снижает требования к хранению. Это снижение связано с тем, что `NCHAR(10)` требует для хранения 20 байт, тогда как `CHAR(10)` требует 10 байт для той же строки Юникод.

Дополнительные сведения см. в статье [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).

В **CTP 2.1** добавлена возможность выбора параметров сортировки UTF-8 по умолчанию во время настройки [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

В **CTP 2.2** добавлена поддержка использования кодировки UTF-8 с репликацией SQL Server.

В **CTP 2.3** добавлена поддержка использования кодировки UTF-8 с параметрами сортировки BIN2 (UTF8_BIN2).

#### <a name="scalar-udf-inlining-ctp-21"></a>Масштабируемое встраивание определяемых пользователем функций (CTP 2.1)

Функция масштабируемого встраивания определяемых пользователем функций автоматически преобразует скалярные функции, определяемые пользователем (UDF), в реляционные выражения и внедряет их в вызывающий SQL-запрос. Это повышает производительность рабочих нагрузок, использующих скалярные функции, определяемые пользователем. Скалярное встраивание определяемых пользователем функций упрощает оптимизацию на основе коэффициентов стоимости в этих функциях. Это позволяет создать эффективные планы с использованием наборов и параллельного выполнения вместо неэффективных планов с последовательным итеративным выполнением. Эта функция включена по умолчанию на уровне совместимости базы данных 150.

Дополнительные сведения см. в разделе [Встраивание скалярных функций, определяемых пользователем](../relational-databases/user-defined-functions/scalar-udf-inlining.md).

#### <a name="a-nametruncation-truncation-error-message-improved-to-include-table-and-column-names-and-truncated-value-ctp-21"></a><a name="truncation" />Улучшенное сообщение об ошибке усечения, которое включает имена таблицы и столбца, а также усеченное значение (CTP 2.1)

Сообщение об ошибке с идентификатором 8152 `String or binary data would be truncated` знакомо многим разработчикам и администраторам [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], которые разрабатывают или поддерживают рабочие нагрузки по перемещению данных. Эта ошибка возникает при передаче данных между исходной и целевой таблицами с различными схемами, когда размер исходных данных превышает размер целевого типа данных. Устранение подобных ошибок может занимать много времени. В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] добавлено новое, более конкретное сообщение об ошибке (2628) для подобного сценария:  

`String or binary data would be truncated in table '%.*ls', column '%.*ls'. Truncated value: '%.*ls'.`

Новое сообщение об ошибке 2628 содержит больше сведений о проблеме с усечением данных, что упрощает процесс устранения ошибки. 

**CTP 2.1 и CTP 2.2** Это сообщение об ошибке активируется явным образом и требует включения [флага трассировки](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 460.

**CTP 2.4** При уровне совместимости базы данных 150 сообщение об ошибке 2628 становится сообщением об усечении по умолчанию, заменяя сообщение об ошибке 8152. Введена новая конфигурация уровня базы данных `VERBOSE_TRUNCATION_WARNINGS`, позволяющая переключаться между сообщениями об ошибках 2628 и 8152 при уровне совместимости базы данных 150. Дополнительные сведения см. в статье [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).
Для уровня совместимости базы данных 140 или более низкого сообщение об ошибке 2628 активируется явным образом и требует включения [флага трассировки](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 460.

#### <a name="improved-diagnostic-data-for-stats-blocking-ctp-21"></a>Улучшенные данные диагностики для блокирующих операций получения статистики (CTP 2.1)

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] предоставляет улучшенные данные диагностики для длительных запросов, которые ожидают завершения синхронных операций обновления статистики. В динамическом административном представлении `sys.dm_exec_requests` столбец `command` отображает `SELECT (STATMAN)`, если `SELECT` ожидает завершения синхронной операции обновления статистики, прежде чем продолжить выполнение запроса. Дополнительно отображается новый тип ожидания `WAIT_ON_SYNC_STATISTICS_REFRESH` в динамическом административном представлении `sys.dm_os_wait_stats`. Он отображает суммарное время на уровне экземпляра, затраченное на синхронные операции обновления статистики.

#### <a name="hybrid-buffer-pool-ctp-21"></a>Гибридный буферный пул (CTP 2.1)

Гибридный буферный пул — это новая возможность ядра СУБД SQL Server, когда доступ к страницам базы данных, хранящимся в файлах базы данных и помещенным в устройство постоянной памяти (PMEM), осуществляется напрямую при необходимости. Поскольку устройства PMEM обеспечивают очень низкую задержку при доступе к данным, ядро может не создавать копию данных в области "чистых таблиц" буферного пула, а просто обращаться к странице напрямую в PMEM. Доступ осуществляется с использованием операций ввода-вывода с привязкой в памяти, подобно компоненту паравиртуализации. Это увеличивает производительность за счет исключения операции копирования страницы в динамическую память и обращения к стеку ввода-вывода операционной системы при доступе к странице в постоянном хранилище. Эта возможность доступна в SQL Server на Windows и Linux.

Дополнительные сведения см. в статье о [гибридном буферном пуле](../database-engine/configure-windows/hybrid-buffer-pool.md).

#### <a name="static-data-masking-ctp-21"></a>Статическое маскирование данных (CTP 2.1)

В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] вводится статическое маскирование данных. Статическое маскирование данных используется для очистки конфиденциальных данных в копиях баз данных SQL Server. Статическое маскирование данных позволяет создать очищенную копию базы данных, в которой все конфиденциальные сведения изменены таким образом, чтобы к этой копии можно было предоставить совместный доступ пользователям вне рабочей среды. Статическое маскирование данных можно использовать для разработки, тестирования, аналитики, бизнес-отчетности, соблюдения нормативных требований, устранения неполадок и других сценариев, при которых определенные данные нельзя копировать в другие среды.

Статическое маскирование данных применяется на уровне столбцов. Выберите столбцы для маскирования и для каждого выбранного столбца укажите функцию маскирования. Операция статического маскирования создает копию базы данных, а затем применяет указанные функции маскирования к столбцам.

##### <a name="static-data-masking-vs-dynamic-data-masking"></a>Отличие статического маскирования данных от динамического

Маскирование данных — это процесс применения маски к базе данных, чтобы скрыть конфиденциальные сведения либо заменить их новыми или очищенными данными. В продуктах Майкрософт поддерживаются две операции маскирования — статическое и динамическое маскирование данных. Динамическое маскирование данных было добавлено в [!INCLUDE[ssSQL16](../includes/sssql16-md.md)]. В следующей таблице сравниваются два решения:

|Статическое маскирование данных |Динамическое маскирование данных|
|:----|:----|
|Выполняется с копией базы данных. <br/><br/>Исходные данные не извлекаются.<br/><br/>Маскирование выполняется на уровне хранилища.<br/><br/>Все пользователи имеют доступ к тем же маскированным данным.<br/><br/>Предназначено для непрерывного доступа для всех членов команды.|Выполняется с исходной базой данных.<br/><br/>Исходные данные не затрагиваются.<br/><br/>Маскирование выполняется оперативно во время исполнения запроса.<br/><br/>Маска зависит от разрешений пользователя. <br/><br/>Предназначено для точного соблюдения прав доступа определенных пользователей.|

#### <a name="database-compatibility-level-ctp-20"></a>Уровень совместимости базы данных (CTP 2.0)

Добавлен **уровень совместимости 150** для базы данных. Чтобы включить этот уровень совместимости для отдельной пользовательской базы данных, выполните команду ниже:

   ```sql
   ALTER DATABASE database_name SET COMPATIBILITY_LEVEL =  150;
   ```

#### <a name="resumable-online-index-create-ctp-20"></a>Возобновляемое создание индексов в подключенном режиме (CTP 2.0)

**Благодаря возобновляемому созданию индексов в подключенном режиме** операцию создания можно остановить и возобновить позже из той точки, где она была приостановлена или завершилась сбоем, а не перезапускать.

Возобновляемое создание индексов в подключенном режиме поддерживает следующие сценарии:
- Возобновление операции создания индекса после сбоя, например после отработки отказа базы данных или заполнения дискового пространства.
- Остановка текущей операции создания индекса и последующее ее восстановление, позволяющее временно освободить системные ресурсы по мере необходимости, а затем восстановить операцию.
- Создание больших индексов без использования большого пространства журнала и длительных транзакций, из-за которых блокируются другие действия по обслуживанию и допускается усечение журнала.

В случае сбоя создания индекса без функции возобновляемости операцию создания индекса в подключенном режиме нужно снова выполнить и полностью перезапустить.

В этом выпуске мы расширим возобновляемые функции, добавив эту функцию в доступную [перестройку возобновляемого индекса в подключенном режиме](http://azure.microsoft.com/blog/modernize-index-maintenance-with-resumable-online-index-rebuild/).

Кроме того, эту функцию можно установить по умолчанию для конкретной базы данных с помощью [стандартного параметра на уровне базы данных для возобновляемых операций DDL и операций DDL в подключенном режиме](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

Дополнительные сведения см. в разделе о [возобновляемых операциях создания индекса в подключенном режиме](../t-sql/statements/create-index-transact-sql.md#resumable-indexes).

#### <a name="build-and-rebuild-clustered-columnstore-indexes-online-ctp-20"></a>Сборка и перестройка кластерных индексов columnstore в подключенном режиме (CTP 2.0)

Преобразуйте таблицы rowstore в формат columnstore. Создание кластеризованных индексов columnstore (CCI) было автономным процессом в предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], что требовало приостановки всех изменений во время создания CCI. [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] и [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] позволяют создать или повторно создать CCI в Интернете. Рабочая нагрузка не будет заблокирована, и все изменения, реализованные в базовых данных, будут прозрачно добавлены в целевую таблицу columnstore. Примеры новых инструкций [!INCLUDE[tsql](../includes/tsql-md.md)], которые можно использовать, приведены ниже.

  ```sql
  CREATE CLUSTERED COLUMNSTORE INDEX cci
    ON <tableName>
    WITH (ONLINE = ON);
  ```

  ```sql
  ALTER INDEX cci
    ON <tableName>
    REBUILD WITH (ONLINE = ON);
  ```

#### <a name="always-encrypted-with-secure-enclaves-ctp-20"></a>Always Encrypted с безопасными анклавами (CTP 2.0)

К Always Encrypted добавляется функция шифрования на месте и полнофункциональные вычисления. Эти расширения связаны с активацией выполнения вычислений с данными в виде открытого текста внутри безопасного анклава на стороне сервера.

Криптографические операции включают шифрование столбцов и смену ключей шифрования столбцов. Эти операции теперь можно запустить с помощью [!INCLUDE[tsql](../includes/tsql-md.md)], и они не требуют перемещения данных из базы данных. Безопасные анклавы обеспечивают шифрование Always Encrypted для более широкого набора сценариев, которые включают следующие требования:  

- Требование защитить конфиденциальные данные от неавторизованных пользователей с привилегиями высокого уровня, включая администраторов баз данных, системных администраторов и операторов облаков, или вредоносных программ.
- Требование того, чтобы в системе базы данных для защищенных данных поддерживались полнофункциональные вычисления.

Дополнительные сведения см. в статье [Always Encrypted с безопасными анклавами](../relational-databases/security/encryption/always-encrypted-enclaves.md).

> [!NOTE]
> Шифрование Always Encrypted с безопасными анклавами доступно только в ОС Windows.

#### <a name="intelligent-query-processing-ctp-20"></a>Интеллектуальная обработка запросов (CTP 2.0)

- **Обратная связь с временно предоставляемым буфером памяти в строковом режиме** — это расширение функции обратной связи с временно предоставляемым буфером памяти, реализованное в [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] путем настройки размеров временно предоставляемого буфера памяти для операторов пакетного и строкового режимов. Для чрезмерных временно предоставляемых буферов памяти, когда предоставленный объем памяти больше чем в два раза превышает объем фактической используемой памяти, функция обратной связи пересчитывает временно предоставляемый буфер памяти. Последовательные выполнения затем будут запрашивать меньше памяти. Для недостаточных временно предоставляемых буферов памяти, которые приводят к временной записи на диск, обратная связь по временно предоставляемому буферу памяти активирует пересчет буфера. Последовательные выполнения затем будут запрашивать больше памяти. Эта функция включена по умолчанию на уровне совместимости базы данных 150.

- Функция **приблизительного COUNT DISTINCT** возвращает приблизительное количество уникальных ненулевых значений в группе. Эта функция предназначена для использования в сценариях больших данных. Она оптимизирована для запросов, если выполняются все приведенные ниже условия:
   - Доступ к наборам данных, содержащим не менее миллиона строк.
   - Агрегирование столбца или столбцов с большим количеством различных значений.
   - Скорость реагирования более важна, чем абсолютная точность.
      - Функция `APPROX_COUNT_DISTINCT` возвращает результаты, которые обычно отклоняются от точного ответа где-то на 2 %.
      - Также эта функция возвращает приблизительный ответ за небольшую часть времени, необходимую для точного ответа.

- **Пакетный режим для данных rowstore** больше не требует индекса columnstore для обработки запроса в пакетном режиме. Пакетный режим позволяет операторам запросов работать с набором строк, а не одной строкой за раз. Эта функция включена по умолчанию на уровне совместимости базы данных 150. Пакетный режим улучшает скорость запросов, обращающихся к таблицам rowstore, если выполняются все приведенные ниже условия:
   - В запросе используются аналитические операторы, такие как соединения или агрегирования.
   - Запрос включает в себя 100 000 или более строк.
   - Запрос ограничен ресурсами ЦП, а не данными ввода и вывода.
   - Создание и использование индекса columnstore включает один из следующих недостатков:
      - Слишком большая нагрузка для запроса.
      - Или же действия не представляются возможными, потому что приложение зависит от функции, которая еще не поддерживается индексами columnstore.

- **Отложенная компиляция табличных переменных** позволяет оптимизировать план и повысить общую производительность для запросов, ссылающихся на табличные переменные. Во время оптимизации и первичной компиляции эта функция будет распространять оценки кратности, основанные на фактическом количестве строк табличной переменной. Эти точные сведения о количестве строк будут использоваться для оптимизации нижестоящих операций планирования. Эта функция включена по умолчанию на уровне совместимости базы данных 150.

Чтобы использовать интеллектуальные функции обработки запросов, установите для базы данных уровень `COMPATIBILITY_LEVEL = 150`.

#### <a id="programmability"></a> Расширения программирования для языка Java (CTP 2.0)

- **Расширение языка Java (предварительная версия)** : используйте расширение языка Java для выполнения кода Java в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] это расширение устанавливается при добавлении в экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] функции "Службы машинного обучения (в базе данных)".

#### <a id="sqlgraph"></a> Функции графа SQL (CTP 2.3)

- **Использование псевдонимов производной таблицы или представления в графовых запросах MATCH (CTP 2.1)** Графовые запросы в [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] (предварительная версия) поддерживают использование псевдонимов для представления и производной таблицы в синтаксисе `MATCH`. Чтобы использовать псевдонимы в `MATCH`, представления и производные таблицы нужно создать в наборе узловых таблиц либо в наборе таблиц ребер при помощи оператора `UNION ALL`. Использование фильтров в узловых таблицах или таблицах ребер не имеет значения. Возможность использовать псевдонимы производных таблиц и представлений в запросах `MATCH` может оказаться полезной в сценариях, когда нужно выполнять запросы по разнородным сущностям или разнородным связям между двумя или несколькими сущностями в графе.

- **Поддержка MATCH в `MERGE` языка DML (CTP 2.0)** позволяет задавать взаимосвязи графа в одной инструкции вместо отдельных инструкций `INSERT`, `UPDATE` или `DELETE`. Объедините текущие данные графа из таблиц узлов или ребер с новыми данными с помощью предикатов `MATCH` в инструкции `MERGE`. Эта функция позволяет использовать сценарии `UPSERT` в таблицах ребер. Теперь пользователи могут использовать одну инструкцию слияния для вставки нового ребра или обновления имеющегося между двумя узлами.

- **Ограничения ребер (CTP 2.0)** добавлены для таблиц ребер в SQL Graph. Таблицы ребер могут соединять любой узел с любым другим узлом в базе данных. С введением ограничений ребер вы теперь можете применить некоторые ограничения для этого поведения. Новое ограничение `CONNECTION` можно использовать для указания типа узлов, которые таблица ребер сможет соединять в схеме. 

  **(CTP 2.3)**  Расширяя эту функцию далее, можно определить действия каскадного удаления для ограничения ребер. Можно определить действия, которые будет предпринимать ядро базы данных, если пользователь удаляет узлы, которые соединяет указанная граница.

#### <a name="database-scoped-default-setting-for-online-and-resumable-ddl-operations-ctp-20"></a>Параметр по умолчанию на уровне базы данных для возобновляемых операций языка DDL и операций языка DDL в подключенном режиме (CTP 2.0)

- **Параметр по умолчанию на уровне базы данных для возобновляемых операций DDL и операций DDL в подключенном режиме** позволяет задать параметр поведения по умолчанию для операций индекса `ONLINE` и `RESUMABLE` на уровне базы данных, а не определять эти параметры для каждой отдельной инструкции языка DDL, например создания или перестройки индекса.

- Установите эти значения по умолчанию с помощью параметров конфигурации на уровне базы данных: `ELEVATE_ONLINE` и `ELEVATE_RESUMABLE`. Оба параметра предписывают ядру автоматически перевести поддерживаемые операции в режим выполнения индекса "в сети" или режим возобновляемого выполнения. Вы можете включить следующие варианты поведения, используя эти параметры:

  - Параметр `FAIL_UNSUPPORTED` позволяет выполнить все операции с индексом (в подключенном режиме или возобновляемые), а операции, которые не поддерживают эти возможности, завершаются сбоем.
  - Параметр `WHEN_SUPPPORTED` позволяет выполнить поддерживаемые операции (в подключенном режиме или возобновляемые), а также запустить операции, которые не поддерживают эти возможности.
  - Параметр `OFF` разрешает текущее поведение выполнения всех операций индекса в автономном режиме и невозобновляемых операций, если в инструкции языка DDL явно не указано другое.

Чтобы переопределить параметр по умолчанию, включите параметр `ONLINE` или `RESUMABLE` в командах создания и перестройки индекса. 

Без этой функции вам необходимо указывать параметры возобновляемых операций и операций в подключенном режиме непосредственно в операторе индекса DDL (например, создание и перестроение индекса).

Дополнительные сведения о возобновляемых операциях с индексами см. в разделе [Возобновляемое создание индексов в подключенном режиме](https://azure.microsoft.com/blog/resumable-online-index-create-is-in-public-preview-for-azure-sql-db/).

#### <a id="ha"></a>Группы доступности Always On — больше синхронных реплик (CTP 2.0)

- **До пяти синхронных реплик.** В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] максимальное количество синхронных реплик увеличено до пяти, по сравнению с тремя в [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Вы можете настроить эту группу из пяти реплик для автоматического перехода на другой ресурс в пределах группы. Предоставляется одна первичная реплика и четыре синхронные вторичные реплики.

- **Перенаправление подключения от вторичной реплики к первичной**: Позволяет направлять подключения клиентских приложений к первичной реплике независимо от целевого сервера, указанного в строке подключения. Эта возможность обеспечивает перенаправление подключения без прослушивателя. Перенаправление подключения от вторичной реплики к первичной можно использовать в следующих случаях:

  - Кластерная технология не предоставляет функцию прослушивателя.
  - Выполняется конфигурация нескольких подсетей, в рамках которой процесс перенаправления усложняется.
  - Сценарии аварийного восстановления или горизонтального масштабирования для чтения с типом кластера `NONE`.

Дополнительные сведения см. в статье [Перенаправление подключения с правами на чтение и запись с вторичной на первичную реплику (группы доступности AlwaysOn)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md).

#### <a name="data-discovery-and-classification-ctp-20"></a>Обнаружение и классификация данных (CTP 2.0)

Обнаружение и классификация данных предоставляют расширенные возможности, изначально встроенные в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Возможность классификации самых важных конфиденциальных данных и присваивания для них меток предоставляет следующие преимущества.
- Позволяет соблюдать стандарты в сфере конфиденциальности данных и нормативных требований.
- Поддерживает сценарии безопасности, такие как мониторинг (аудит) и оповещение о необычном доступе к конфиденциальным данным.
- Упрощает определение размещения конфиденциальных данных в организации, благодаря чему администраторы могут предпринимать необходимые меры для защиты базы данных.

Дополнительные сведения см. в статье [Обнаружения и классификация данных SQL](../relational-databases/security/sql-data-discovery-and-classification.md).

[Возможности аудита](../relational-databases/security/auditing/sql-server-audit-database-engine.md) также были расширены. Теперь в журнал аудита добавлено новое поле под названием `data_sensitivity_information`, в котором указывается классификация конфиденциальности (метки) фактических данных, возвращенных запросом. Дополнительные сведения и примеры см. в статье о [добавлении классификации конфиденциальности](../t-sql/statements/add-sensitivity-classification-transact-sql.md).

>[!NOTE]
>Условия включения аудита не изменились. К записям аудита добавлено новое поле (`data_sensitivity_information`), в котором указывается классификация конфиденциальности (метки) фактических данных, возвращенных запросом. Дополнительные сведения см. в разделе, [посвященном контролю за доступом к конфиденциальным данным](/azure/sql-database/sql-database-data-discovery-and-classification/#subheading-3).

#### <a name="expanded-support-for-persistent-memory-devices-ctp-20"></a>Расширенная поддержка устройств с постоянной памятью (CTP 2.0)

Любой файл [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], размещенный в постоянной памяти устройства, теперь может работать в режиме *паравиртуализации*. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] напрямую получает доступ к устройству путем обхода стека хранилища операционной системы с помощью эффективных операций memcpy. Этот режим повышает производительность, так как при его использовании сокращается задержка операций ввода-вывода на таких устройствах.
    - Примеры файлов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:
        - Файлы баз данных
        - Файлы журнала транзакций
        - Файлы контрольных точек OLTP, выполняющейся в памяти.
    - Постоянная память также называется памятью класса хранилища.
    - На некоторых веб-сайтах сторонних производителей постоянную память иногда неформально называют *pmem*.

> [!NOTE]
> В этой предварительной версии компонент паравиртуализации файлов в постоянной памяти доступен только для Linux. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Windows поддерживает устройства постоянной памяти начиная с [!INCLUDE[ssSQL15](../includes/sssql15-md.md)].

#### <a name="support-for-columnstore-statistics-in-dbcc-clonedatabase-ctp-20"></a>Поддержка статистики columnstore в DBCC CLONEDATABASE (CTP 2.0)

`DBCC CLONEDATABASE` позволяет создать копию только схемы базы данных, содержащую все элементы, необходимые для устранения проблем с производительностью запросов без копирования данных. В предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] эта команда не копировала данные статистики, необходимые для точного устранения неполадок с запросами индекса columnstore, и для получения этих сведений требовалось выполнять некоторые действия вручную. В этой версии [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] `DBCC CLONEDATABASE` автоматически собирает большие двоичные объекты статистики индексов columnstore, что позволяет не выполнять дополнительные действия вручную.

#### <a name="new-options-added-to-spestimatedatacompressionsavings-ctp-20"></a>К sp_estimate_data_compression_savings добавлены новые параметры (CTP 2.0)

`sp_estimate_data_compression_savings` возвращает текущий размер запрошенного объекта и оценивает размер объекта для запрошенного состояния сжатия. Сейчас эта процедура поддерживает три параметра: `NONE`, `ROW` и `PAGE`. В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] представлены два новых параметра: `COLUMNSTORE` и `COLUMNSTORE_ARCHIVE`. Эти новые параметры позволят оценить экономию места при создании индекса columnstore в таблице, для которой применяется стандартное или архивное сжатие данных columnstore.

#### <a id="ml"></a>Отказоустойчивые кластеры Служб машинного обучения SQL Server и моделирование на основе разделов (CTP 2.0)

- **Моделирование на основе разделов**. Обработка внешних сценариев на каждый раздел данных с использованием новых параметров, добавленных в `sp_execute_external_script`. Эта функция поддерживает обучение нескольких небольших моделей (одна модель на раздел данных) вместо одной большой.

- **Отказоустойчивый кластер Windows Server**: Настройка высокого уровня доступности для Служб машинного обучения в отказоустойчивом кластере Windows Server.

Дополнительные сведения см. в статье [Новые возможности служб машинного обучения SQL Server](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

#### <a name="lightweight-query-profiling-infrastructure-enabled-by-default-ctp-20"></a>Упрощенная инфраструктура профилирования запросов включена по умолчанию (CTP 2.0)

Упрощенная инфраструктура профилирования запросов (LWP) предоставляет более эффективные данные производительности запросов по сравнению со стандартными механизмами профилирования. Сейчас упрощенное профилирование включено по умолчанию. Эта возможность представлена в [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] с пакетом обновления 1. Упрощенное профилирование предоставляет механизм сбора статистики выполнения запросов с ожидаемыми издержками ресурсов ЦП 2 %, по сравнению с издержками ЦП до 75 % для стандартного механизма профилирования запросов. В предыдущих версиях эта функция была выключена по умолчанию. Администраторы баз данных могут включить ее с помощью [флага трассировки 7412](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). 

Дополнительные сведения об облегченном профилировании см. в разделе [Инфраструктура профилирования запросов](../relational-databases/performance/query-profiling-infrastructure.md).

В **CTP 2.3** введена новая конфигурация уровня базы данных `LIGHTWEIGHT_QUERY_PROFILING`, позволяющая включить или отключить инфраструктуру профилирования упрощенных запросов.

#### <a id="polybase"></a>Новые соединители PolyBase

- **Новые соединители для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata и MongoDB.** В [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] вводятся новые соединители с внешними данными для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata и MongoDB.

#### <a name="new-sysdmdbpageinfo-system-function-returns-page-information-ctp-20"></a>Новая системная функция sys.dm_db_page_info возвращает сведения о странице (CTP 2.0)

`sys.dm_db_page_info(database_id, file_id, page_id, mode)` возвращает сведения о странице в базе данных. Эта функция возвращает строку, содержащую данные заголовка страницы, включая `object_id`, `index_id` и `partition_id`. В большинстве случаев эта функция заменяет потребность в использовании `DBCC PAGE`. 

Чтобы упростить устранение задержек, связанных со страницей, к `sys.dm_exec_requests` и `sys.sysprocesses` также добавлен новый столбец с именем page_resource. Этот новый столбец позволяет объединить `sys.dm_db_page_info` с этими представлениями с помощью другой новой системной функции — `sys.fn_PageResCracker`. Рассмотрите следующий сценарий в качестве примера:

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d 
  CROSS APPLY sys.fn_PageResCracker(d.page_resource) AS r
  CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id,'DETAILED')
    AS page_info;
```

### <a id="sqllinux"></a>SQL Server на Linux

- **Группа доступности AlwaysOn в контейнерах Docker с Kubernetes (CTP 2.2)** : Kubernetes позволяет управлять контейнерами, в которых запущены экземпляры [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], для обеспечения высокой доступности набора баз данных с помощью групп доступности SQL Server AlwaysOn. Оператор Kubernetes развертывает набор с отслеживанием состояния, включая контейнер с **контейнером mssql-server** и монитор работоспособности.

- **Новый реестр контейнеров (CTP 2.1)** : Все образы контейнеров для [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], а также [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] теперь находятся в реестре контейнеров Майкрософт. Реестр контейнеров Майкрософт — это официальный реестр контейнеров для распределения контейнеров продукта корпорации Майкрософт. Кроме того, теперь опубликованы сертифицированные образы на основе Red Hat Enterprise Linux (RHEL).

  - Реестр контейнеров Майкрософт: `mcr.microsoft.com/mssql/server:vNext-CTP2.0`
  - Сертифицированные образы контейнеров на основе RHEL: `mcr.microsoft.com/mssql/rhel/server:vNext-CTP2.0`

- **Поддержка репликации (CTP 2.0)** : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] поддерживает репликацию SQL Server на платформе Linux. Виртуальная машина Linux с установленным агентом SQL может быть издателем, распространителем или подписчиком. 

  Создайте следующие типы публикаций:
  - Транзакционная
  - Моментальный снимок
  - Объединить

  Настройте репликацию [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] или используйте [хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

- **Поддержка координатора распределенных транзакций (Майкрософт) (MSDTC) (CTP 2.0)** . Эта служба поддерживается в [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] на платформе Linux. Дополнительные сведения см. в статье о [настройке MSDTC на платформе Linux](../linux/sql-server-linux-configure-msdtc.md).

- **Поддержка OpenLDAP для сторонних поставщиков AD (CTP 2.0)** : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] в Linux поддерживает OpenLDAP, что позволяет сторонним поставщикам использовать Active Directory.

- **Машинное обучение в Linux (CTP 2.0)** . Теперь службы машинного обучения [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] (в базе данных) поддерживаются и в Linux. Предусмотрена также поддержка хранимой процедуры `sp_execute_external_script`. Инструкции по установке служб машинного обучения на платформе Linux см. в статье [Установка служб машинного обучения [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] с поддержкой R и Python на платформе Linux](../linux/sql-server-linux-setup-machine-learning.md).

### <a id="mds"></a> Master Data Services 

- **Элементы управления Silverlight заменены элементами HTML (CTP 2.0)** : Теперь портал Master Data Services (MDS) не зависит от Silverlight. Все прежние компоненты Silverlight заменены элементами управления HTML.

### <a id="security"></a>безопасность

- **Управление сертификатами в диспетчере конфигурации SQL Server (CTP 2.0)** : Сертификаты SSL/TLS широко используются для обеспечения безопасного доступа к экземплярам SQL Server. Управление сертификатами интегрировано в диспетчер конфигурации SQL Server, что упрощает выполнение таких распространенных задач:

  - Просмотр и проверка сертификатов, установленных в экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 
  - Просмотр сертификатов, срок действия которых истекает.
  - Развертывание сертификатов на компьютерах, участвующих в группах доступности AlwaysOn (из узла, содержащего первичную реплику).
  - Развертывание сертификатов на компьютерах, участвующих в экземпляре отказоустойчивого кластера (из активного узла).

  > [!NOTE]
  > Пользователю необходимо предоставить разрешения администратора на всех узлах кластера.

### <a id="tools"></a>Инструменты

- [**Azure Data Studio**](../azure-data-studio/what-is.md): Ранее выпущенное в режиме предварительной версии под названием SQL Operations Studio средство Azure Data Studio представляет собой современный упрощенный кроссплатформенный рабочий стол с открытым исходным кодом для выполнения самых распространенных задач в области разработки и администрирования данных. С помощью Azure Data Studio и [расширения предварительной версии [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](../azure-data-studio/sql-server-2019-extension.md) можно подключаться к SQL Server в локальной среде и в облаке на платформах Windows, macOS и Linux. Azure Data Studio позволяет:

<a name = "tools-ctp23"></a>

  - Использовать AAD. (CTP-версия 2.3)
  - Представление пользовательского интерфейса записной книжки было перемещено в ядро Azure Data Studio. (CTP-версия 2.3)
  - Добавлен новый мастер создания внешних источников данных из распределенной файловой системы Hadoop (HDFS) в кластере больших данных SQL Server. (CTP-версия 2.3)
  - Улучшен пользовательский интерфейс средства просмотра записной книжки. (CTP-версия 2.3)
  - Добавлены новые интерфейсы API записной книжки. (CTP-версия 2.3)
  - Добавлена команда "Переустановить зависимости записной книжки" с обновлениями пакета Python. (CTP-версия 2.3)
  - Подключение и управление для кластеров больших данных в [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. (CTP 2.1)
  - Редактировать и выполнять запросы в современной среде разработки с помощью невероятно быстрой функции Intellisense, фрагментов кода и путем интеграции управления исходным кодом. (CTP 2.0) 
  - Быстро визуализировать данные с помощью встроенных диаграмм результирующих наборов. (CTP 2.0)
  - Создавать настраиваемые панели мониторинга для серверов и баз данных с помощью настраиваемых мини-приложений. (CTP 2.0)  
  - Легко управлять более широкими средами с помощью встроенного терминала. (CTP 2.0)
  - Анализировать данные, работая с записной книжкой, интегрированной в Jupyter. (CTP 2.0)
  - Улучшить работу с пользовательскими расширениями и темами (CTP 2.0).
  - Изучить ресурсы Azure с помощью встроенных подписки и обозревателя ресурсов. (CTP 2.0)
  - Поддерживать сценарии, в которых используется кластер больших данных SQL Server. (CTP 2.0)
  
  > [!TIP]
  > Наиболее актуальные улучшения Azure Data Studio см. в разделе [Заметки о выпуске Azure Data Studio](../azure-data-studio/release-notes-azure-data-studio.md).

- [**SQL Server Management Studio (SSMS) 18.0 (предварительная версия)** ](../ssms/sql-server-management-studio-ssms.md): поддерживает [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

  - Запустить Azure Data Studio можно из SSMS. (CTP-версия 2.3)
  - Поддержка функции Always Encrypted с безопасными анклавами. (CTP 2.0)
  - Более компактный файл для скачивания. (CTP 2.0)
  - Теперь работает на основе изолированной оболочки Visual Studio 2017. (CTP 2.0)
  - Полный список см. в разделе, посвященном [изменениям SSMS](../ssms/release-notes-ssms.md). (CTP 2.0)

- [**Модуль SQL Server PowerShell**](http://www.powershellgallery.com/packages/SqlServer/21.1.18080): Модуль SqlServer PowerShell позволяет разработчикам SQL Server, администраторам и специалистам по BI автоматизировать развертывание баз данных и управление серверами.

  - Обновите версию 21.0 до 21.1 для поддержки SMO версии 150.
  - Обновлен поставщик SQL Server (SQLRegistration) для отображения групп IS, AS и RS.
  - Устранена проблема в командлете `New-SqlAvailabilityGroup` при разработке для SQL Server 2014.
  - Добавлен параметр `–LoadBalancedReadOnlyRoutingList` в `Set-SqlAvailabilityReplica` и `New-SqlAvailabilityReplica`.
  - Командлет `AnalysisService` обновлен, чтобы можно было использовать кэшированный токен входа из `Login-AzureAsAccount` для служб Azure Analysis Services.

### <a id="ssas"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services (SSAS) 

#### <a name="many-to-many-ctp24"></a>Связи "многие ко многим" в табличных моделях (CTP 2.4)

Эта функция позволяет устанавливать связи "многие ко многим" между неуникальными столбцами в разных таблицах. Связь можно определить между измерением и таблицей фактов со степенью детализации выше, чем ключевой столбец измерения. Это избавляет от необходимости нормализовать таблицы измерений и повышает удобство работы для пользователей, так как итоговая модель содержит меньше таблиц, а столбцы в них логически сгруппированы. В этом выпуске CTP 2.4 связи "многие ко многим" представляют собой функцию на уровне ядра. 

Для связей "многие ко многим" требуются модели на уровне совместимости 1470. В настоящее время они поддерживаются только в [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.3 и более поздних версиях. В этом выпуске CTP 2.4 связи "многие ко многим" можно создавать с помощью API табличной модели объектов (TOM), языка скриптов табличной модели (TMSL) и редактора табличных моделей с открытым кодом. Поддержка в SQL Server Data Tools (SSDT) будет добавлена в будущем выпуске, как и документация. Дополнительные сведения об этом и других выпусках компонентов CTP-версии будут предоставляться в блоге служб Analysis Services.

#### <a name="property-ctp24"></a>Параметры памяти для регуляции ресурсов (CTP 2.4)

Описанные здесь параметры памяти уже доступны в Azure Analysis Services. Начиная с версии CTP 2.4 они также поддерживаются службами [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Analysis Services. 

- **Memory\QueryMemoryLimit** — с помощью этого свойства памяти можно ограничивать очереди памяти, которые создаются запросами DAX к модели. 
- **DbpropMsmdRequestMemoryLimit** — с помощью этого свойства XMLA можно переопределять значение свойства сервера Memory\QueryMemoryLimit для подключения.
- **OLAP\Query\RowsetSerializationLimit** — это свойство сервера ограничивает количество строк, возвращаемых в наборе строк, защищая ресурсы сервера от чрезмерно интенсивного использования экспорта данных. Оно применимо как к запросам DAX, так и к запросам многомерных выражений.

Эти свойства можно задавать с помощью последней версии SQL Server Management Studio (SSMS). Дополнительные сведения об этой функции будут предоставлены в блоге служб Analysis Services.

#### <a name="calc-ctp24"></a>Группы вычисления в табличных моделях (CTP-версия 2.3). 

Группы вычисления решают распространенную проблему в сложных моделях, где может присутствовать большое число мер на основе одних и тех же вычислений, таких как логика операций со временем. Группы вычисления отображаются в клиентских отчетах как таблица с одним столбцом. Каждое значение в столбце представляет многократно используемое вычисление, или элемент вычисления, которое может применяться к любой из мер.  

Группа вычисления может содержать любое число элементов вычисления. Каждый элемент вычисления определяется с помощью выражения DAX. Добавлены три новые функции DAX для работы с группами вычисления. 

- `SELECTEDMEASURE()` — возвращает ссылку на меру в текущем контексте.  

- `SELECTEDMEASURENAME()` — возвращает строку, содержащую имя меры в текущем контексте.  

- `ISSELECTEDMEASURE(M1, M2, …)` — возвращает логическое значение, указывающее, является ли мера в текущем контексте одной из тех, что заданы в качестве аргумента.

Помимо новых функций DAX, представлены два новых динамических административных представления:

- `TMSCHEMA_CALCULATION_GROUPS`  
- `TMSCHEMA_CALCULATION_ITEMS`  

##### <a name="limitations-in-this-release"></a>Ограничения в этом выпуске:

- Функция `ALLSELECTED DAX` пока не поддерживается.
- Безопасность на уровне строк в таблице групп вычисления пока не поддерживается.
- Безопасность на уровне объектов в таблице групп вычисления пока не поддерживается.
- Выражения DetailsRows, ссылающиеся на элементы вычисления, пока не поддерживаются.
- MDX пока не поддерживается.

##### <a name="known-issues-in-this-release"></a>Известные проблемы в этом выпуске:

- Наличие групп вычисления в модели может приводить к возвращению мерами типов данных variant, из-за чего могут происходить сбои обновления вычисляемых столбцов и таблиц, которые ссылаются на меры.

##### <a name="compatibility-level"></a>Уровень совместимости

Для групп вычисления требуются модели на уровне совместимости 1470. В настоящее время они поддерживаются только в [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.3 и более поздних версиях. На текущий момент группы вычисления могут создаваться с помощью API табличной модели объектов (TOM), языка скриптов табличной модели (TMSL) и редактора табличных моделей с открытым кодом. Поддержка в SQL Server Data Tools (SSDT) будет добавлена в будущем выпуске, как и документация. Дополнительные сведения об этом и других выпусках компонентов CTP-версии будут предоставляться в блоге служб Analysis Services.

## <a name="see-also"></a>См. также раздел

- [`SqlServer` Модуль PowerShell](https://www.powershellgallery.com/packages/Sqlserver)
- [Документация по SQL Server PowerShell](../powershell/sql-server-powershell.md)

## <a name="next-steps"></a>Следующие шаги

- [Заметки о выпуске [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](sql-server-ver15-release-notes.md).

- [Майкрософт [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]: Технический документ](http://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Опубликовано в сентябре 2018 г. Применяется к CTP-версии 2.0 Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] для контейнеров Windows, Linux и Docker.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
