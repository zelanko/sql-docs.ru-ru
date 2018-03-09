---
title: "Новые возможности в ядре СУБД SQL Server 2016 | Документация Майкрософт"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: database-engine
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [SQL Server Database Engine]
- Database Engine [SQL Server], what's new
ms.assetid: 8f625d5a-763c-4440-97b8-4b823a6e2439
caps.latest.revision: "431"
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Active
ms.openlocfilehash: 0e5018b6b111790d2ff0415180e0608798da44ac
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="whats-new-in-database-engine---sql-server-2016"></a>Новые возможности в ядре СУБД SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

В этом разделе описаны усовершенствования, представленные в выпуске [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].  В этом выпуске появились новые средства и усовершенствования, которые расширяют возможности и повышают производительность архитекторов, разработчиков и администраторов, занимающихся проектированием, созданием и обслуживанием систем хранения данных.

Новые возможности других компонентов SQL Server см. в разделе [Что нового в SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md).

> [!NOTE]
>  [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] — это 64-разрядное приложение. 32-разрядная установка больше не поддерживается, хотя некоторые элементы работают как 32-разрядные.

#### <a name="try-it-out"></a>Попробуйте продукт

- Чтобы скачать [!INCLUDE[ssSQL15](../includes/sssql15-md.md)], перейдите на сайт **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**![скачать](../analysis-services/media/download.png "скачать").

- Есть учетная запись Azure?  Тогда перейдите **[сюда](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/)** , чтобы запустить виртуальную машину с уже установленным [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] .

> [!NOTE]
> Заметки о текущем выпуске приводятся в разделе [Заметки о выпуске SQL Server 2016](../sql-server/sql-server-2016-release-notes.md).
  
## <a name="sql-server-2016-service-pack-1-sp1"></a>SQL Server 2016 с пакетом обновления 1 (SP1)  
-  Синтаксис `CREATE OR ALTER <object>` теперь доступен для [процедур](../t-sql/statements/create-procedure-transact-sql.md), [представлений](../t-sql/statements/create-view-transact-sql.md), [функций](../t-sql/statements/create-function-transact-sql.md) и [триггеров](../t-sql/statements/create-trigger-transact-sql.md).
-   Добавлена поддержка более общей модели указаний запросов: `OPTION (USE HINT('<hint1>', '<hint2>'))`. Дополнительные сведения см. в разделе [Указания запросов (Transact-SQL)](../t-sql/queries/hints-transact-sql-query.md).  
- Добавлено динамическое административное представление [sys.dm_exec_valid_use_hints](../relational-databases/system-dynamic-management-views/sys-dm-exec-valid-use-hints-transact-sql.md) для перечисления указаний.  
- Добавлено динамическое административное представление [sys.dm_exec_query_statistics_xml](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md) для возврата промежуточной статистики XML для showplan.  
- Добавлено динамическое административное представление [sys.dm_db_incremental_stats_properties](../relational-databases/system-dynamic-management-views/sys-dm-db-incremental-stats-properties-transact-sql.md) для добавочной статистики по указанной таблице.  
- В [sys.dm_server_services](../relational-databases/system-dynamic-management-views/sys-dm-server-services-transact-sql.md) добавлен столбец `instant_file_initialization_enabled`.  
- В [sys.dm_exec_query_profiles](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md) добавлен столбец `estimated_read_row_count`.  
-  В [sys.dm_os_sys_info](../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md) добавлены столбцы `sql_memory_model` и `sql_memory_model_desc` для предоставления сведений о модели блокировки для страниц памяти.
-  Список выпусков, которые поддерживают ряд функций, был расширен. К ним относятся: безопасность на уровне строк, Always Encrypted, динамическая маскировка данных, аудит базы данных, OLTP в памяти и несколько других функций во всех выпусках. Дополнительные сведения см. в статье [Возможности, поддерживаемые различными выпусками SQL Server 2016](../sql-server/editions-and-supported-features-for-sql-server-2016.md).   
-  [sp_refresh_parameter_encryption](../relational-databases/system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) поддерживает шифрование AlwaysOn для обновления метаданных при переопределении объектов, зашифрованных с помощью AlwaysOn.  


##  <a name="Feature"></a> SQL Server 2016 RTM
В этом разделе содержатся следующие подразделы:

-   [Индексы columnstore](#columnstore)
-   [Конфигурации в области базы данных](#scopedconfiguration)
-   [Выполняющаяся в памяти OLTP](#InMemory)
-   [Оптимизатор запросов](#QueryOptimizer)
-   [Динамическая статистика запросов](#LiveStats)
-   [Хранилище запросов](#QueryStore)
-   [Темпоральные таблицы](#TT)
-   [Чередующееся резервное копирование в хранилище больших двоичных объектов Microsoft Azure](#StripedBackupToAzure)
-   [Резервное копирование моментальных снимков файлов в хранилище больших двоичных объектов Microsoft Azure](#FileSnapshotBackup)
-   [Управляемое резервное копирование](#ManagedBackup)
-   [База данных TempDB](#multipleTempDB)
-   [Встроенная поддержка JSON](#ForJson)
-   [PolyBase](#bkPolyBase)
-   [База данных Stretch](#stretch)
-   [Поддержка UTF-8](#UTF8)
-   [Новый размер базы данных по умолчанию и значения автоувеличения](#DefaultDB)
-   [Улучшения Transact-SQL](#TSQL)
-   [Улучшения системного представления](#SystemTable)
-   [Улучшения в системе безопасности](#Security)
-   [Улучшения высокого уровня доступности](#HighAvailability)
-   [Усовершенствования репликации](#Repl)
-   [Улучшенные инструменты](#Tools)

####  <a name="columnstore"></a> Индексы columnstore

В этом выпуске представлено несколько усовершенствований индексов columnstore, включая обновляемые некластеризованные индексы columnstore, индексы columnstore таблиц в памяти и многие другие возможности для оперативной аналитики.

- Индекс columnstore только для чтения может изменяться после обновления.  Для этого перестроение индекса не требуется.

- Улучшена производительность аналитических запросов для индексов columnstore, особенно для статистических выражений и строковых предикатов.

- Улучшена поддержка динамических административных представлений и XEvents.

Дополнительные сведения см. в разделе [Руководство по индексам columnstore](../relational-databases/indexes/columnstore-indexes-overview.md) электронной документации:

- [Сводка функций индексов columnstore по версиям](~/relational-databases/indexes/columnstore-indexes-what-s-new.md) — описание новых возможностей.

- [Загрузка данных индексов columnstore](../relational-databases/indexes/columnstore-indexes-data-loading-guidance.md)

- [Производительность запросов индексов columnstore](~/relational-databases/indexes/columnstore-indexes-query-performance.md)

- [Начало работы с Columnstore для получения операционной аналитики в реальном времени](../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)

- [Индексы сolumnstore для хранилищ данных](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)

- [Дефрагментация индексов columnstore](~/relational-databases/indexes/columnstore-indexes-defragmentation.md)


####  <a name="scopedconfiguration"></a> Конфигурации в области базы данных


Новая инструкция [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) позволяет контролировать отдельные конфигурации для определенной базы данных. Параметры конфигурации влияют на работу приложения.

Новая инструкция доступна как в [!INCLUDE[ssSQL15](../includes/sssql15-md.md)], так и в [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)].



####  <a name="InMemory"></a> Выполняющаяся в памяти OLTP


##### <a name="storage-format-change"></a>Изменение формата хранения

Формат хранения таблиц, оптимизированных для памяти, в версиях SQL Server 2014 и 2016 отличается. Для обновления и присоединения/восстановления из SQL Server 2014 во время восстановления базы данных сериализуется новый формат хранения, а база данных перезапускается.

- [Обновление до SQL Server 2016](../database-engine/install-windows/upgrade-sql-server.md)


##### <a name="alter-table-is-log-optimized-and-runs-in-parallel"></a>Инструкция ALTER TABLE оптимизирована для журнала и выполняется параллельно

Теперь при выполнении инструкции ALTER TABLE применительно к оптимизированной для памяти таблице в журнал записываются только изменения метаданных. Это существенно сокращает интенсивность ввода-вывода для журнала. Кроме того, в большинстве сценариев инструкция ALTER TABLE теперь выполняется параллельно, что может значительно сократить длительность ее выполнения.

- Сведения о непараллельных исключениях, включая объекты LOB, см. в разделе [Изменение таблиц с оптимизацией для памяти](../relational-databases/in-memory-oltp/altering-memory-optimized-tables.md).



##### <a name="statistics"></a>Статистика

[Статистика для таблиц, оптимизированных для памяти,](../relational-databases/in-memory-oltp/statistics-for-memory-optimized-tables.md) теперь обновляется автоматически. Кроме того, выборка теперь является поддерживаемым методом сбора статистики, который позволяет избежать более затратного метода полного сканирования.


##### <a name="parallel-and-heap-scan-for-memory-optimized-tables"></a>Параллельное сканирование и сканирование кучи для таблиц, оптимизированных для памяти

Все таблицы, оптимизированные для памяти, и индексы в них теперь поддерживают параллельное сканирование. Это повышает производительность аналитических запросов.

Кроме того, поддерживается сканирование, которое может выполняться параллельно. В случае с таблицей, оптимизированной для памяти, сканирование кучи означает сканирования всех строк таблицы с помощью структуры данных кучи в памяти, используемой для хранения строк. Для полного сканирования таблицы сканирование кучи эффективнее использования индекса.

##### <a name="transact-sql-improvements-for-memory-optimized-tables"></a>Улучшения Transact-SQL для таблиц, оптимизированных для памяти

Ряд элементов Transact-SQL, которые не поддерживались для оптимизированных для памяти таблиц в SQL Server 2014, теперь поддерживаются в SQL Server 2016.


- Поддерживаются ограничения и индексы UNIQUE.


- Поддерживаются ссылки FOREIGN KEY между оптимизированными для памяти таблицами.
  - Внешние ключи могут ссылаться только на первичный ключ, но не на уникальный.


- Поддерживаются ограничения CHECK.

- В ключе неуникального индекса могут допускаться значения NULL.

- В оптимизированных для памяти таблицах поддерживаются триггеры.
  - Поддерживаются только триггеры AFTER. Триггеры INSTEADOF не поддерживаются.
  - Все триггеры в таблице, оптимизированной для памяти, должны использовать WITH NATIVE_COMPILATION.

- Полная поддержка всех кодовых страниц SQL Server, параметров сортировки с индексами и других артефактов в таблицах, оптимизированных для памяти, а также модулях, скомпилированных в собственном коде T-SQL.


- Поддержка [изменения оптимизированных для памяти таблиц](../relational-databases/in-memory-oltp/altering-memory-optimized-tables.md):
  - операций ADD и DROP с индексами; Изменение bucket_count для хэш-индексов.
  - Внесение изменений в схему: добавление, удаление, изменение столбцов, а также добавление и удаление ограничения.

- Оптимизированная для памяти таблица теперь может содержать несколько столбцов, суммарная длина которых превышает длину страницы размером 8060 байт. Примером является таблица с тремя столбцами типа `nvarchar(4000)`. В таких ситуациях некоторые столбцы теперь хранятся вне строки. Вашим запросам не нужно знать, находится ли столбец в строке или вне строки.

- [Типы больших объектов (LOB)](../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md) `varbinary(max)`, `nvarchar(max)` и `varchar(max)` теперь поддерживаются в таблицах, оптимизированных для памяти.


Общие сведения см. в следующих разделах:

- [Конструкции языка Transact-SQL, неподдерживаемые в In-Memory OLTP](../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)
- [Неподдерживаемые функции SQL Server для выполняющейся в памяти OLTP](~/relational-databases/in-memory-oltp/unsupported-sql-server-features-for-in-memory-oltp.md)


##### <a name="transact-sql-improvements-for-natively-compiled-modules"></a>Улучшения Transact-SQL для модулей, скомпилированных в собственном коде

Ряд элементов Transact-SQL, которые не поддерживались для модулей, скомпилированных в собственном коде, в SQL Server 2014, теперь поддерживаются в SQL Server 2016.


- Конструкции запросов:
  - UNION и UNION ALL
  - SELECT DISTINCT
  - OUTER JOIN
  - Вложенные запросы в SELECT


- Инструкции INSERT, UPDATE и DELETE теперь могут содержать [предложение OUTPUT](../t-sql/queries/output-clause-transact-sql.md).

- Объекты LOB теперь можно использовать в собственной процедуре следующими способами:
  - для объявления переменных;
  - для получения входных параметров.
  - в качестве параметров, передаваемых в строковые функции, такие как LTrim или Substring, в собственной процедуре.


- Встроенные (то есть содержащие одну инструкцию) функции с табличными значениями теперь можно компилировать в собственном коде.

- Определяемые пользователем скалярные функции теперь можно компилировать в собственном коде.

- Расширена поддержка вызова в собственных процедурах следующих функций:
  - встроенных [функций безопасности](../t-sql/functions/security-functions-transact-sql.md);
  - встроенных [математических функций](../t-sql/functions/mathematical-functions-transact-sql.md);
  - Встроенная функция `@@SPID`.


- Теперь поддерживается EXECUTE AS CALLER, поэтому предложение EXECUTE AS при создании модуля, скомпилированного в собственном коде T-SQL, больше не требуется.


Общие сведения см. в следующих разделах:

- [Поддерживаемые функции для модулей, скомпилированных в собственном коде T-SQL](../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)
- [Изменение скомпилированных в собственном коде модулей T-SQL](../relational-databases/in-memory-oltp/altering-natively-compiled-t-sql-modules.md)


##### <a name="performance-and-scaling-improvements"></a>Улучшения производительности и масштабируемости

- Больше нет никаких ограничений для размера данных. См. раздел [Оценка требований к объему памяти для таблиц, оптимизированных для памяти](~/relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md).

- За [сохранение изменений в таблицах, оптимизированных для памяти, на диске](../relational-databases/in-memory-oltp/scalability.md) теперь отвечают несколько параллельных потоков.

- Поддержка параллельного плана для [доступа к таблицам, оптимизированным для памяти, с помощью интерпретируемых инструкций Transact-SQL](../relational-databases/in-memory-oltp/accessing-memory-optimized-tables-using-interpreted-transact-sql.md).


##### <a name="enhancements-in-sql-server-management-studio"></a>Улучшения среды SQL Server Management Studio

- Для [определения того, должна ли таблица или хранимая процедура быть перенесена в выполняющуюся в памяти OLTP,](../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) больше не требуется настройка сборщиков данных или хранилища данных управления. Теперь можно запустить отчет непосредственно для производственной базы данных.

- [Командлет PowerShell для оценки миграции](../relational-databases/in-memory-oltp/powershell-cmdlet-for-migration-evaluation.md) позволяет оценить пригодность нескольких объектов к миграции в базу данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

- Создание контрольных списков миграции: щелкните базу данных правой кнопкой мыши и выберите пункт "Задачи" > "Создать контрольные списки миграции OLTP в памяти".

##### <a name="cross-feature-support"></a>Поддержка различных компонентов

- Поддержка использования временных систем управления версиями с In-Memory OLTP. Дополнительные сведения см. в разделе [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md).

- Поддержка хранения запросов для собственного кода из рабочих нагрузок In-Memory OLTP. Дополнительные сведения см. в разделе [Использование хранилища запросов с выполняющейся в памяти OLTP](../relational-databases/performance/using-the-query-store-with-in-memory-oltp.md).

- [Безопасность на уровне строк в оптимизированных для памяти таблицах](../relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables.md#rls)

- Подключения, [использующие множественные активные результирующие наборы (MARS)](../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md), теперь могут получить доступ к таблицам, оптимизированным для памяти, и скомпилированным в собственном коде хранимым процедурам.

- Поддержка [прозрачного шифрования данных](../relational-databases/security/encryption/transparent-data-encryption.md). Если база данных настроена для шифрования, файлы в [файловой группе, оптимизированной для памяти,](../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md) теперь также шифруются.

Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).


####  <a name="QueryOptimizer"></a> Оптимизатор запросов
##### <a name="compatibility-level-guarantees"></a>Гарантии уровня совместимости
При обновлении базы данных до SQL Server 2016 изменения плана не отображаются, если вы остаетесь на более ранних уровнях совместимости, которые вы использовали (например, 120 или 110). Новые функции и усовершенствования, связанные с оптимизатором запросов, доступны только на последнем уровне совместимости. 
##### <a name="trace-flag-4199"></a>Флаг трассировки 4199
В общем случае вам не нужно использовать флаг трассировки 4199 в SQL Server 2016, так как большинство типов поведения оптимизатора запросов, которые контролируются этим флагом, включаются безусловно на последнем уровне совместимости (130) в SQL Server 2016.
##### <a name="new-referential-integrity-operator"></a>Оператор ссылочной целостности
Максимальное количество таблиц и столбцов, на которые может ссылаться таблица в качестве внешних ключей (исходящих ссылок), равно 253. [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] увеличивает ограничение на количество других таблиц и столбцов, которые могут ссылаться на столбцы в одной таблице (входящие ссылки), с 253 до 10 000. Ограничения см. в разделе [Create Foreign Key Relationships](../relational-databases/tables/create-foreign-key-relationships.md). Представлен новый оператор ссылочной целостности (на уровне совместимости 130), который выполняет проверки целостности ссылок на месте. Это повышает общую производительность для операций UPDATE и DELETE в таблицах, имеющих большое число входящих ссылок, тем самым позволяя использовать большое число входящих ссылок. Дополнительные сведения см. в разделе [Query Optimizer Additions in SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/05/23/query-optimizer-additions-in-sql-server/)(Дополнения для оптимизатора запросов в SQL Server 2016).
##### <a name="parallel-update-of-sampled-statistics"></a>Параллельное обновление статистики по выборке
Выборка данных для формирования статистики теперь выполняется в параллельном режиме (на уровне совместимости 130), что повышает производительность сбора статистики. Дополнительные сведения см. в разделе [Статистика обновлений](../t-sql/statements/update-statistics-transact-sql.md).
#### <a name="sublinear-threshold-for-update-of-statistics"></a>Сублинейное пороговое значение для обновления статистики
Автоматическое обновление статистики для больших таблиц стало более агрессивным (на уровне совместимости 130). Начиная с SQL Server 2016, пороговое значение запуска автоматического обновления статистики составляет 20 %, для больших таблиц оно начинает уменьшаться (по-прежнему в процентном отношении) по мере увеличения числа строк в таблице. Вам больше не нужно устанавливать флаг трассировки 2371 для уменьшения порогового значения. 
##### <a name="other-enhancements"></a>Другие усовершенствования
Вставка в инструкции Insert-select является многопотоковой или может использовать параллельный план (при уровне совместимости 130). Для получения параллельного плана инструкция INSERT … SELECT должна использовать указание TABLOCK. Дополнительные сведения см. в статье [Parallel Insert Select](https://blogs.msdn.microsoft.com/sqlcat/2016/07/06/sqlsweet16-episode-3-parallel-insert-select/)(Выбор параллельной вставки).

####  <a name="LiveStats"></a> Динамическая статистика запросов
 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] позволяет просматривать динамический план выполнения активного запроса. Этот динамический план запроса позволяет анализировать процесс выполнения запроса в режиме реального времени по мере передачи управления от одного оператора плана запроса другому. Дополнительные сведения см. в статье [Live Query Statistics](../relational-databases/performance/live-query-statistics.md).

####  <a name="QueryStore"></a> Хранилище запросов
Хранилище запросов — это новый компонент, который предоставляет администраторам баз данных подробные сведения о выборе и производительности плана запросов. Оно упрощает устранение неполадок с производительностью, позволяя быстро находить разницу в производительности, вызванную изменениями в планах запросов. Функция автоматически записывает журнал запросов, планы и статистику выполнения и сохраняет их для просмотра. Она разделяет данные по временным окнам, позволяя просмотреть шаблоны использования и понять, когда изменения плана запросов произошли на сервере. Хранилище запросов предоставляет сведения, используя диалоговое окно [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] , и позволяет принудительно выполнять запрос к одному из выбранных планов запроса. Дополнительные сведения см. в разделе [Monitoring Performance By Using the Query Store](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).


####  <a name="TT"></a> Темпоральные таблицы
[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] теперь поддерживает темпоральные таблицы с системным управлением версиями. Темпоральная таблица — это новый тип таблицы, которая содержит точные сведения о хранимых фактах в любой момент времени. Каждая темпоральная таблица на самом деле состоит из двух таблиц: одной для текущих данных и одной для данных журнала. Система гарантирует, что при изменении данных в таблице с текущими данными предыдущие значения сохраняются в таблице журнала. Предоставлены конструкции запросов, чтобы упростить работу пользователей. Дополнительные сведения см. в разделе [Temporal Tables](../relational-databases/tables/temporal-tables.md).

####  <a name="StripedBackupToAzure"></a> Чередующееся резервное копирование в хранилище больших двоичных объектов Microsoft Azure
В [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] резервное копирование SQL Server по URL-адресу с помощью службы хранилища BLOB-объектов Microsoft Azure теперь поддерживает наборы чередующихся резервных копий с использованием блочных BLOB-объектов. При этом максимальный размер резервных копий составляет 12,8 ТБ. Примеры см. в разделе [Code Examples](../relational-databases/backup-restore/sql-server-backup-to-url.md#Examples).

####  <a name="FileSnapshotBackup"></a> Резервное копирование моментальных снимков файлов в хранилище больших двоичных объектов Microsoft Azure
 В [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] резервное копирование SQL Server по URL-адресу теперь поддерживает использование моментальных снимков Azure для резервного копирования баз данных, в которых все файлы хранятся с помощью службы хранилища BLOB-объектов Microsoft Azure. Дополнительные сведения см. в разделе [Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md).

####  <a name="ManagedBackup"></a> Управляемое резервное копирование
В [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SQL Server управляемое резервное копирование в Microsoft Azure использует новое хранилище блочных BLOB-объектов для файлов резервных копий. Кроме того, представлено несколько изменений и усовершенствований управляемого резервного копирования.

-   Поддержка автоматического и настраиваемого планирования резервного копирования.

-   Поддержка резервного копирования системных баз данных.

-   Поддержка баз данных, использующих простую модель восстановления.

 Дополнительные сведения см. в разделе [SQL Server Managed Backup to Microsoft Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).

> [!NOTE]
>  В [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] эти новые функции управляемого резервного копирования еще не поддерживаются в пользовательском интерфейсе [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].

####  <a name="multipleTempDB"></a> База данных TempDB
 Предоставлено несколько улучшений базы данных TempDB.

-   Флаги трассировки 1117 и 1118 больше не требуются для базы данных tempdb. Если существует несколько файлов базы данных tempdb, размер всех файлов будет увеличиваться в одно и то же время в зависимости от параметров роста. Кроме того, все выделения в базе данных tempdb будут использовать однородные экстенты.

-   По умолчанию программа установки добавляет число файлов tempdb, равное количеству ЦП, или 8 файлов в зависимости от того, какое значение меньше.

-   Во время установки можно настроить количество файлов базы данных tempdb, исходный размер, автоувеличение и размещение каталога с помощью нового элемента управления вводом в пользовательском интерфейсе в разделе "Настройка компонента Database Engine — TempDB" мастера установки SQL Server.

-   Исходный размер по умолчанию — 8 МБ, а автоматическое увеличение по умолчанию — 64 МБ.

-   Можно указать несколько томов для файлов базы данных tempdb. Если указано несколько каталогов, файлы данных tempdb будут распределяться по каталогам циклическим перебором.

####  <a name="ForJson"></a> Встроенная поддержка JSON
В SQL Server 2016 появилась встроенная поддержка импорта и экспорта данных JSON и работы со строками JSON. Эта встроенная поддержка распространяется на перечисленные ниже инструкции и функции.

-   Форматирование результатов запроса или их экспорт в формате JSON путем добавления предложения **FOR JSON** в инструкцию **SELECT** . Например, предложение **FOR JSON** позволяет делегировать форматирование выходных данных JSON из клиентских приложений в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).

-   Преобразование данных JSON в строки и столбцы либо импорт данных JSON с помощью функции **OPENJSON** поставщика набора строк. Используйте **OPENJSON** , чтобы преобразовать данные JSON в SQL Server или в строки и столбцы для приложений или служб, которые не могут использовать JSON напрямую. Дополнительные сведения см. в статье [Преобразование данных JSON в строки и столбцы с помощью функции OPENJSON (SQL Server)](../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md).

-   Функция **ISJSON** проверяет наличие допустимых данных JSON в строке. Дополнительные сведения см. в разделе [ISJSON (Transact-SQL)](../t-sql/functions/isjson-transact-sql.md)

-   Функция **JSON_VALUE** извлекает скалярное значение из строки JSON. Дополнительные сведения см. в разделе [JSON_VALUE (Transact-SQL)](../t-sql/functions/json-value-transact-sql.md).

-   Функция **JSON_QUERY** извлекает объект или массив из строки JSON. Дополнительные сведения см. в разделе [JSON_QUERY (Transact-SQL)](../t-sql/functions/json-query-transact-sql.md).

-   Функция **JSON_MODIFY** обновляет значение свойства в строке JSON и возвращает обновленную строку JSON. Дополнительные сведения см. в разделе [JSON_MODIFY &#40;Transact-SQL&#41;](../t-sql/functions/json-modify-transact-sql.md).

####  <a name="bkPolyBase"></a> PolyBase
 PolyBase позволяет использовать инструкции T-SQL для доступа и обращения к данным, хранящимся в Hadoop или хранилище BLOB-объектов Azure, с использованием нерегламентированных запросов. Кроме того, эта технология позволяет запрашивать частично структурированные данные и объединять результаты с реляционными наборами данных, хранящимися в SQL Server. Технология PolyBase оптимизирована для рабочих нагрузок хранилищ данных и предназначена для сценариев с аналитическими запросами.

 Дополнительные сведения см. в [руководстве по PolyBase](../relational-databases/polybase/polybase-guide.md).

####  <a name="stretch"></a> База данных Stretch
 База данных Stretch — это новая функция [!INCLUDE[ssSQL15](../includes/sssql15-md.md)], которая прозрачно и безопасно переносит исторические данные в облако Microsoft Azure. Вы можете получать полный доступ к данным SQL Server, будь то локальным или распространенным на облако. Вы устанавливаете политику, которая определяет место хранения данных, а SQL Server обрабатывает перемещение данных в фоновом режиме. Вся таблица всегда подключена к сети и доступна для запросов. Кроме того, база данных Stretch не требует изменений в существующих запросах или приложениях — место хранения данных абсолютно прозрачно для приложения. Дополнительные сведения см. в разделе [Stretch Database](../sql-server/stretch-database/stretch-database.md).
 
####  <a name="UTF8"></a> Поддержка UTF-8
[bcp Utility](../tools/bcp-utility.md), [BULK INSERT](../t-sql/statements/bulk-insert-transact-sql.md) и [OPENROWSET](../t-sql/functions/openrowset-transact-sql.md) теперь поддерживают кодовую страницу UTF-8. Дополнительные сведения см. в этих разделах и в разделе [Создание файла форматирования (SQL Server)](../relational-databases/import-export/create-a-format-file-sql-server.md).

####  <a name="DefaultDB"></a> Новый размер базы данных по умолчанию и значения автоувеличения
Новые значения шаблона базы данных и значения по умолчанию для новых баз данных (которые основаны на шаблоне). Исходный размер файлов данных и журнала теперь составляет 8 МБ. По умолчанию размер автоматического увеличения файлов данных и журнала теперь составляет 64 МБ.


###  <a name="TSQL"></a> Улучшения Transact-SQL
Многочисленные улучшения для поддержки функций, описанных в других подразделах этого раздела. Доступны следующие дополнительные усовершенствования.
- Инструкция TRUNCATE TABLE теперь допускает усечение указанных секций. Дополнительные сведения см. в разделе [TRUNCATE TABLE (Transact-SQL)](../t-sql/statements/truncate-table-transact-sql.md).
- [ALTER TABLE (Transact-SQL)](../t-sql/statements/alter-table-transact-sql.md) теперь позволяет выполнять многие действия по изменению столбцов с сохранением доступности таблицы.
- Динамическое административное представление полнотекстового индекса [sys.dm_fts_index_keywords_position_by_document (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-position-by-document-transact-sql.md) возвращает расположение ключевых слов в документах. Это представление, кроме того, было добавлено в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] SP2 и [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] SP1.
- Новое указание запроса **NO_PERFORMANCE_SPOOL** позволяет предотвратить добавление оператора очередей в планы запроса. Это может повысить производительность при выполнении нескольких параллельных запросов с операциями очередей. Дополнительные сведения см. в разделе [Указания запросов (Transact-SQL)](../t-sql/queries/hints-transact-sql-query.md).
- Инструкция [FORMATMESSAGE &#40;Transact-SQL&#41;](../t-sql/functions/formatmessage-transact-sql.md) теперь принимает аргумент msg_string.
- Максимальный размер ключа индекса для НЕКЛАСТЕРИЗОВАННЫХ индексов увеличен до 1700 байт.
- Добавлен новый синтаксис DROP IF для инструкций удаления, связанных с AGGREGATE, ASSEMBLY, COLUMN, CONSTRAINT, DATABASE, DEFAULT, FUNCTION, INDEX, PROCEDURE, ROLE, RULE, SCHEMA, SECURITY POLICY, SEQUENCE, SYNONYM, TABLE, TRIGGER, TYPE, USER и VIEW. Описание синтаксиса см. в отдельных разделах, посвященных синтаксису.
- Параметр MAXDOP добавлен в [DBCC CHECKTABLE (Transact-SQL)](../t-sql/database-console-commands/dbcc-checktable-transact-sql.md), [DBCC CHECKDB (Transact-SQL)](../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) и [DBCC CHECKFILEGROUP (Transact-SQL)](../t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql.md) для указания степени параллелизма.
- Теперь можно указать значение SESSION_CONTEXT. Включает функцию [SESSION_CONTEXT (Transact-SQL)](../t-sql/functions/session-context-transact-sql.md), функцию [CURRENT_TRANSACTION_ID (Transact-SQL)](../t-sql/functions/current-transaction-id-transact-sql.md) и процедуру [sp_set_session_context (Transact-SQL)](../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md).
- Расширения углубленной аналитики позволяют пользователям запускать скрипты, написанные на поддерживаемом языке, например R. [!INCLUDE[tsql](../includes/tsql-md.md)] поддерживает R благодаря хранимой процедуре [sp_execute_external_script (Transact-SQL)](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) и [параметру конфигурации сервера external scripts enabled](../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md). Дополнительные сведения см. в разделе [SQL Server R Services](../advanced-analytics/r-services/sql-server-r-services.md).
- Дополнительная поддержка R: возможность создания пула внешних ресурсов. Дополнительные сведения см. в разделе [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](../t-sql/statements/create-external-resource-pool-transact-sql.md).  Новые представления каталогов и динамические административные представления ([sys.resource_governor_external_resource_pools (Transact-SQL)](../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md) и [sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)). Доступны дополнительные аргументы для [sp_execute_external_script (Transact-SQL)](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) и [CREATE WORKLOAD GROUP (Transact-SQL)](../t-sql/statements/create-workload-group-transact-sql.md). Дополнительные столбцы добавлены в некоторые существующие представления каталога регулятора ресурсов и динамические административные представления.
- В синтаксис [CREATE USER](../t-sql/statements/create-user-transact-sql.md) добавлен параметр ALLOW_ENCRYPTED_VALUE_MODIFICATIONS для поддержки функции Always Encrypted. Дополнительные сведения см. в разделе [Перенос конфиденциальных данных с помощью функции постоянного шифрования](../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md).
- Функции [COMPRESS (Transact-SQL)](../t-sql/functions/compress-transact-sql.md) и [DECOMPRESS (Transact-SQL)](../t-sql/functions/decompress-transact-sql.md) преобразуют значения для алгоритма GZIP.
- Функции [DATEDIFF_BIG (Transact-SQL)](../t-sql/functions/datediff-big-transact-sql.md) и [AT TIME ZONE (Transact-SQL)](../t-sql/queries/at-time-zone-transact-sql.md), а также представление [sys.time_zone_info (Transact-SQL)](../relational-databases/system-catalog-views/sys-time-zone-info-transact-sql.md) добавлены для поддержки взаимодействия с датами и временем.
- Учетные данные теперь можно создать на уровне базы данных (в дополнение к учетным данным на уровне сервера, которые были доступны ранее). Дополнительные сведения см. в разделе [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../t-sql/statements/create-database-scoped-credential-transact-sql.md).
- Восемь новых свойств добавлены в [SERVERPROPERTY (Transact-SQL)](../t-sql/functions/serverproperty-transact-sql.md): InstanceDefaultDataPath, InstanceDefaultLogPath, ProductBuild, ProductBuildType, ProductMajorVersion, ProductMinorVersion, ProductUpdateLevel и ProductUpdateReference.
- Ограничение на ввод в 8000 байт для функции [HASHBYTES (Transact-SQL)](../t-sql/functions/hashbytes-transact-sql.md) снято.
- Добавлены новые строковые функции [STRING_SPLIT (Transact-SQL)](../t-sql/functions/string-split-transact-sql.md) и [STRING_ESCAPE (Transact-SQL)](../t-sql/functions/string-escape-transact-sql.md).
- Параметры автоматического увеличения: флаг трассировки 1117 заменен параметрами AUTOGROW_SINGLE_FILE и AUTOGROW_ALL_FILES инструкции ALTER DATABASE, при этом флаг трассировки 1117 не оказывает никакого влияния. Дополнительные сведения см. в разделе [Параметры инструкции ALTER DATABASE для файлов и файловых групп (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md) и в описании нового столбца is_autogrow_all_files представления [sys.filegroups (Transact-SQL)](../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md).
- Выделение смешанных экстентов: для пользовательских баз данных выделение первых 8 страниц объекта по умолчанию изменится с использования смешанных экстентов страниц на использование однородных экстентов. Флаг трассировки 1118 заменяется параметром ЗАДАТЬ инструкции MIXED_PAGE_ALLOCATION ALTER DATABASE, при этом флаг трассировки 1118 не оказывает никакого влияния. Дополнительные сведения см. в разделе [Параметры ALTER DATABASE SET (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-set-options.md), и в описании нового столбца `is_mixed_page_allocation_on` представления [sys.databases (Transact-SQL)](../relational-databases/system-catalog-views/sys-databases-transact-sql.md).


###  <a name="SystemTable"></a> Улучшения системного представления
- Два новых представления поддерживают безопасность на уровне строк. Дополнительные сведения см. в разделах [sys.security_predicates (Transact-SQL)](../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md) и [sys.security_policies (Transact-SQL)](../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md).
- Семь новых представлений поддерживает хранилище запросов. Дополнительные сведения см. в разделе [Представления каталога хранилища запросов (Transact-SQL)](../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md).
- В [sys.dm_exec_query_stats (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md) добавлены 24 новых столбца со сведениями о временно предоставляемом буфере памяти.
- Для новых указания запроса (MIN_GRANT_PERCENT и MAX_GRANT_PERCENT) добавлены для определения временно предоставляемых буферов памяти. См. раздел [Указания запросов (Transact-SQL)](../t-sql/queries/hints-transact-sql-query.md).
- [sys.dm_exec_session_wait_stats (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-exec-session-wait-stats-transact-sql.md) предоставляет отчет для каждого сеанса аналогично [sys.dm_os_wait_stats (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md) для всего сервера.
- [sys.dm_exec_function_stats (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-exec-function-stats-transact-sql.md) предоставляет статистику выполнения касательно скалярных функций.
- Начиная с версии [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] записи в [sys.dm_db_index_usage_stats (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md) сохраняются, как и до выпуска [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)].
- Сведения об инструкциях, отправленных экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], могут быть возвращены новой функцией динамического управления [sys.dm_exec_input_buffer (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-exec-input-buffer-transact-sql.md).
- Два новых представления поддерживают [службы R SQL Server](../advanced-analytics/r-services/sql-server-r-services.md): [sys.dm_external_script_requests](../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) и [sys.dm_external_script_execution_stats](../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). 


###  <a name="Security"></a> Улучшения в системе безопасности

####  <a name="RLS"></a> Безопасность на уровне строк
Безопасность на уровне строк представляет управление доступом на основе предиката. Он поддерживает гибкую централизованную оценку на основе предиката, которая может учитывать метаданные (например, метки) или другие критерии, определяемые администратором по своему усмотрению. Предикат используется как критерий для определения, имеет ли пользователь соответствующий доступ к данным на основе атрибутов пользователя. Управление доступом на основе метки можно реализовать с помощью управления доступом на основе предиката. Дополнительные сведения см. в разделе [Безопасность на уровне строк](../relational-databases/security/row-level-security.md).


####  <a name="TCE"></a> Always Encrypted
С технологией Always Encrypted [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может выполнять операции с зашифрованными данными, и, что самое главное, ключ шифрования хранится вместе с приложением в доверенной среде клиента, а не на сервере. Постоянное шифрование защищает данные клиента, поэтому у администраторов баз данных нет доступа к данным в виде обычного текста. Шифрование и расшифровка данных происходит прозрачно на уровне драйвера, что сводит к минимуму изменения, которые необходимо внести в существующие приложения. Дополнительные сведения см. в разделе [Постоянное шифрование (компонент Database Engine)](../relational-databases/security/encryption/always-encrypted-database-engine.md).


####  <a name="Masking"></a> Динамическое маскирование данных
Динамическое маскирование данных ограничивает возможность раскрытия конфиденциальных данных за счет маскирования этих данных для непривилегированных пользователей. Динамическое маскирование данных помогает предотвратить несанкционированный доступ к конфиденциальным данным, позволяя клиентам определить объем раскрываемых конфиденциальных данных с минимальным влиянием на уровень приложения. Эта функция безопасности на основе политики скрывает конфиденциальные данные в результирующем наборе запроса в заданных полях базы данных, а данные в базе данных не меняются. Дополнительные сведения см. в разделе [Dynamic Data Masking](../relational-databases/security/dynamic-data-masking.md).


####  <a name="Perms"></a> Новые разрешения
- Разрешение **ALTER ANY SECURITY POLICY** доступно как часть реализации безопасности на уровне строк.
- Разрешения **ALTER ANY MASK** и **UNMASK** доступны как часть реализации маскирования динамических данных.
- Разрешения **ALTER ANY COLUMN ENCRYPTION KEY**, **VIEW ANY COLUMN ENCRYPTION KEY**, **ALTER ANY COLUMN MASTER KEY DEFINITION**и **VIEW ANY COLUMN MASTER KEY DEFINITION** доступны как часть реализации постоянного шифрования.
- Разрешения **ALTER ANY EXTERNAL DATA SOURCE** и **ALTER ANY EXTERNAL FILE FORMAT** являются видимыми в [!INCLUDE[ssSQL15](../includes/sssql15-md.md)], но применяются только к [!INCLUDE[ssAPS](../includes/ssaps-md.md)] ([!INCLUDE[ssDW](../includes/ssdw-md.md)]).
- Разрешения **EXECUTE ANY EXTERNAL SCRIPT** доступны в рамках поддержки скриптов R.
 - Разрешения **ALTER ANY DATABASE SCOPED CONFIGURATION** доступны для авторизации использования инструкции [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

####  <a name="TDE"></a> Прозрачное шифрование данных
- Добавлена поддержка аппаратного ускорения Intel AES-NI для прозрачного шифрования данных. Это позволяет снизить загрузку ЦП при включении прозрачного шифрования данных.

###  <a name="AES"></a> Шифрование AES для конечных точек
- Шифрование по умолчанию для конечных точек изменено с RC4 на AES.

####  <a name="newcredentialtype"></a> Новый тип учетных данных
- Учетные данные теперь можно создать на уровне базы данных (в дополнение к учетным данным на уровне сервера, которые были доступны ранее). Дополнительные сведения см. в разделе [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../t-sql/statements/create-database-scoped-credential-transact-sql.md).


###  <a name="HighAvailability"></a> Улучшения высокого уровня доступности
SQL Server 2016 Standard Edition теперь поддерживает базовые группы доступности AlwaysOn. Основные группы доступности предоставляют поддержку для первичной и вторичной реплики. Эта возможность заменяет устаревшую технологию зеркального отображения базы данных для обеспечения высокой доступности. Дополнительные сведения о различиях между базовыми и дополнительными группами доступности см. в разделе [Основные группы доступности (группы доступности AlwaysOn)](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md).

Балансировка нагрузки для запросов соединений с намерением чтения теперь поддерживается в наборе реплик только для чтения. Раньше подключения всегда направлялись к первой доступной реплике только для чтения в списке маршрутов. Дополнительные сведения см. в разделе [Настройка балансировки нагрузки между репликами только для чтения](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md#loadbalancing).

 Число реплик, которые поддерживают автоматический переход на другой ресурс, был увеличен с двух до трех.

 Теперь групповые управляемые учетные записи служб поддерживаются для отказоустойчивых кластеров AlwaysOn. Дополнительные сведения см. в разделе [Групповые управляемые учетные записи служб](https://technet.microsoft.com/library/hh831782.aspx). Для Windows Server 2012 R2 требуется обновление, чтобы избежать временного простоя после изменения пароля. Чтобы получить обновление, изучите раздел [Службы на основе gMSA не могут войти в систему после изменения пароля в домене Windows Server 2012 R2](https://support.microsoft.com/kb/2998082/).

 [!INCLUDE[ssHADR](../includes/sshadr-md.md)] поддерживает распределенные транзакции и службу DTC в Windows Server 2016. Дополнительные сведения см. в разделе [Поддержка распределенных транзакций](../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md#dtcsupport).

 Теперь вы можете настроить [!INCLUDE[ssHADR](../includes/sshadr-md.md)] для отработки отказа, когда база данных переходит в автономный режим. Для этого изменения требуется установить для параметра **DB_FAILOVER** значение **ON** в инструкции [CREATE AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md) или [ALTER AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/alter-availability-group-transact-sql.md).

AlwaysOn теперь поддерживает зашифрованные базы данных. Мастеры группы доступности теперь запрашивают пароль для всех баз данных, которые содержат главный ключ базы данных, при создании новой группы доступности или при добавлении баз данных или реплик в существующую группу доступности.

Теперь две группы доступности в двух отдельных отказоустойчивых кластерах (WSFC) могут быть объединены в распределенную группу доступности. Дополнительные сведения см. в разделе [Распределенные группы доступности (группы доступности AlwaysOn)](../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md).

Прямое присвоение начальных значений позволяет автоматически инициализировать вторичную реплику по сети (вместо ручного заполнения, для которого необходимо восстановить физическую резервную копию целевой базы данных во вторичной реплике). Прямое присвоение начальных значений задается параметром **SEEDING_MODE=AUTOMATIC** в инструкции [CREATE AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md) или [ALTER AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/alter-availability-group-transact-sql.md). Кроме того, необходимо указать **GRANT CREATE ANY DATABASE** с [ALTER AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/alter-availability-group-transact-sql.md) во вторичной реплике, используемой с прямой инициализацией.

**Улучшение производительности:** пропускная способность синхронизации групп доступности повысилась примерно в 10 раз благодаря параллельному и более быстрому сжатию блоков журнала в первичной реплике, оптимизированному протоколу синхронизации, а также параллельной распаковке и повтору записей журнала во вторичной реплике. Это позволило повысить актуальность доступных для чтения вторичных реплик и сократить время восстановления базы данных в случая отработки отказа. Обратите внимание на то, что повтор оптимизированных для памяти таблиц пока не выполняется параллельно в SQL Server 2016.

###  <a name="Repl"></a> Усовершенствования репликации
- Теперь поддерживается репликация таблиц, оптимизированных для памяти. Дополнительные сведения см. в разделе [Репликация на подписчиков оптимизированных для памяти таблиц](../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md).
- Теперь поддерживается репликация в [!INCLUDE[ssSDSFull](../includes/sssdsfull-md.md)]. Дополнительные сведения см. в разделе [Replication to SQL Database](../relational-databases/replication/replication-to-sql-database.md).

###  <a name="Tools"></a> Улучшенные инструменты

####  <a name="SSMS"></a> Среда Management Studio
Скачайте последнюю версию [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)

- [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] поддерживает библиотеку проверки подлинности Active Directory (ADAL), которая находится в стадии разработки для подключения к Microsoft Azure. Она заменяет проверку подлинности на основе сертификатов, используемую в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].
- Для установки [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] требуется платформа .NET 4.6. Платформа .NET 4.6 устанавливается автоматически, если устанавливается компонент [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .
- Новый параметр сетки результатов запроса поддерживает сохранение возврата каретки и перевода строки (символов новой строки) при копировании и сохранении текста из сетки результатов. Это можно настроить в меню "Сервис — Параметры".
- Средства управления SQL Server больше не устанавливаются из дерева основных компонентов. Дополнительные сведения см. в разделе [Установка средств управления SQL Server со средой SSMS](http://msdn.microsoft.com/library/af68d59a-a04d-4f23-9967-ad4ee2e63381).
- Для установки [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] требуется платформа .NET 4.6.1. Платформа .NET 4.6.1 устанавливается автоматически, если устанавливается компонент [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .

####  <a name="UA"></a> Помощник по обновлению
SQL Server 2016 Upgrade Advisor Preview — это автономное средство, которое позволяет пользователям предыдущих версий применять набор правил обновления для базы данных SQL Server, чтобы выявить сбои, изменения поведения и нерекомендуемые функции, а также получить справку по внедрению новых функций, таких как база данных Stretch.

 Вы можете скачать Upgrade Advisor Preview [здесь](https://www.microsoft.com/en-us/download/details.aspx?id=48119) или установить его с помощью установщика веб-платформы.

## <a name="see-also"></a>См. также:
[Что нового в SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)
 
[Заметки о выпуске SQL Server 2016](../sql-server/sql-server-2016-release-notes.md) 
 
[Установка средств управления SQL Server со средой SSMS](http://msdn.microsoft.com/library/af68d59a-a04d-4f23-9967-ad4ee2e63381)








