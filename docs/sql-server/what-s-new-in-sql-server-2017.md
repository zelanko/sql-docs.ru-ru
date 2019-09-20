---
title: Новые возможности в SQL Server 2017 | Microsoft Docs
ms.custom: ''
ms.date: 10/20/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 0b57f375-9242-4bb2-9d4b-c560d5a93524
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 87537979ab3459727f07aec460118a74e15561f9
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874822"
---
# <a name="whats-new-in-sql-server-2017"></a>Новые возможности в SQL Server 2017
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]
SQL Server 2017 — это важный шаг к созданию универсальной платформы SQL Server, которая позволит вам свободно выбирать языки разработки, типы данных, локальные или облачные среды и операционные системы, обеспечивая совместимость с Linux, контейнерами Docker на базе Linux и с Windows. Этот раздел содержит сводку о новых возможностях в отдельных функциональных областях, а также ссылки на дополнительные сведения. Дополнительные сведения о SQL Server в Linux см. в [документации по SQL Server в Linux](https://docs.microsoft.com/sql/linux/).

[![Скачать в центре оценки ПО](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?LinkID=829477) **Попробуйте:** [Скачать выпуск SQL Server 2017 за октябрь 2017 г.](https://go.microsoft.com/fwlink/?LinkID=829477)

> [!NOTE]
> Помимо приведенных ниже изменений следует отметить накопительные обновления, которые регулярно выпускаются после выхода общедоступной версии. Эти накопительные обновления содержат много усовершенствований и исправлений. Сведения о последнем выпуске накопительного обновления см в разделе [Накопительные обновления SQL Server 2017](https://aka.ms/sql2017cu).

## <a name="sql-server-2017-database-engine"></a>Ядро СУБД SQL Server 2017

SQL Server 2017 включает множество новых функций, усовершенствований и улучшений работы для ядра СУБД. 
- **Сборки CLR** теперь можно добавлять в список доверенных в качестве обходного пути для функции `clr strict security`, описанной в CTP 2.0. Для поддержки списка доверенных сборок (RC1) добавлены функции [sp_add_trusted_assembly](../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md), [sp_drop_trusted_assembly](../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) и [sys.trusted_assemblies](../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md).  
- **Возобновляемая перестройка индексов в подключенном режиме**: позволяет возобновить эту операцию с момента остановки после сбоя (например, при отработке отказа в реплику или нехватке места на диске) либо приостановить и возобновить ее позже. В разделе [ALTER INDEX](../t-sql/statements/alter-index-transact-sql.md) и [руководящие принципы для операций с индексами в сети](../relational-databases/indexes/guidelines-for-online-index-operations.md). (CTP 2.0)
- Параметр **IDENTITY_CACHE** для ALTER DATABASE SCOPED CONFIGURATION позволяет избежать пропусков в значениях столбцов удостоверений при непредвиденной перезагрузке или отработке отказа сервера на вторичный сервер. В разделе [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). (CTP 2.0)
- Новое поколение функций обработки запросов, использующих стратегии оптимизации для адаптации к среде выполнения рабочих нагрузок ваших приложений. В первую версию семейства функций для **адаптивной обработки запросов** мы включили три улучшения: **адаптивные соединения в пакетном режиме**, **обратная связь по временно предоставляемому буферу памяти в пакетном режиме** и **выполнение с чередованием** для многооператорных функций с табличными значениями.  См. статью [Интеллектуальная обработка запросов в базах данных SQL](../relational-databases/performance/intelligent-query-processing.md).
- **Автоматическая настройка базы данных** предоставляет сведения о возможных проблемах с обработкой запросов и рекомендуемые решения. Она также может автоматически исправлять выявленные проблемы. См. раздел [Automatic tuning](../relational-databases/automatic-tuning/automatic-tuning.md) (Автоматическая настройка). (CTP 2.0)
- Новые **возможности для баз данных графов**, предназначенные для моделирования связей "многие ко многим", включают новый синтаксис [CREATE TABLE](../t-sql/statements/create-table-sql-graph.md) для создания граничных таблиц и таблиц узлов, а также ключевое слово [MATCH](../t-sql/queries/match-sql-graph.md) для запросов. См. раздел [Graph Processing with SQL Server 2017](../relational-databases/graphs/sql-graph-overview.md) (Работа с графами в SQL Server 2017). (CTP 2.0)
- Параметр sp_configure, который называется `clr strict security`, включен по умолчанию для повышения безопасности сборок CLR. См. раздел [CLR strict security](../database-engine/configure-windows/clr-strict-security.md). (CTP 2.0)
- Программа установки теперь позволяет задать для каждого файла tempdb начальный размер до **256 ГБ** (262 144 МБ). Если размер файла превышает 1 ГБ, а мгновенная инициализация файлов не включена, выдается соответствующее предупреждение. (CTP 2.0)
- Столбец **modified_extent_page_count** в [sys.dm_db_file_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md) отслеживает разностные изменения в каждом файле базы данных, что позволяет использовать интеллектуальные решения для полного или разностного резервного копирования, основываясь на проценте измененных страниц базы данных. (CTP 2.0)
- Синтаксис T-SQL [SELECT INTO](../t-sql/queries/select-into-clause-transact-sql.md) теперь поддерживает загрузку таблицы в файловую группу, отличную от пользовательской группы по умолчанию, с помощью ключевого слова **ON**. (CTP 2.0)
- Теперь поддерживаются транзакции между всеми базами данных, входящими в **группу доступности AlwaysOn**, включая базы данных, являющиеся частью одного экземпляра. См. раздел [Transactions - Always On Availability Groups and Database Mirroring](../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md) (Транзакции — группы доступности AlwaysOn и зеркальное отображение баз данных) (CTP 2.0)
- Новые функции для **Групп доступности** включают поддержку чтения и масштабирования без кластера, параметр минимального числа реплик для фиксации, возможности миграции между Windows и Linux и тестирование на обеих системах. (CTP 1.3)
- Новые динамические административные представления:
    - [sys.dm_db_log_stats](../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md) предоставляет сводку атрибутов и сведения о файлах журналов транзакций, которые помогают контролировать работоспособность в журналах транзакций. (CTP 2.1)
    - [sys.dm_tran_version_store_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-space-usage.md) отслеживает использование хранилища версий для каждой базы данных, что помогает оперативно планировать размеры tempdb. (CTP 2.0)
    - [sys.dm_db_log_info](../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md) предоставляет сведения о виртуальных файлах журнала (VLF) для отслеживания возможных проблем с журналами транзакций, оповещения об этих проблемах и их предотвращения. (CTP 2.0)
    - [sys.dm_db_stats_histogram](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) — это новое динамическое административное представление для анализа статистики. (CTP 1.3)
    - **sys.dm_os_host_info** предоставляет сведения об операционной системе для Windows и Linux. (CTP 1.0)
- Инструмент **Database Tuning Advisor (DTA)** получил дополнительные функции и более высокую производительность. (CTP 1.2)
- **Усовершенствования работы в памяти** включают поддержку вычисляемых столбцов в оптимизированных для памяти таблицах, а также полную поддержку функций JSON и оператор CROSS APPLY для модулей, скомпилированных в собственном коде. (CTP 1.1)
- Новые **строковые функции**: CONCAT_WS, TRANSLATE и TRIM, а для функции STRING_AGG теперь поддерживается WITHIN GROUP. (CTP 1.1)
- Появились новые **параметры массового доступа** (BULK INSERT и OPENROWSET(BULK...)) для файлов CSV и BLOB-файлов Azure. (CTP 1.1)
- **Улучшения работы с оптимизированными для памяти объектами** включают sp_spaceused и устранение ограничения в 8 индексов для оптимизированных для памяти таблиц, sp_rename для этих таблиц и для скомпилированных в собственном коде модулей T-SQL, а также CASE и TOP (N) WITH TIES для скомпилированных в собственном коде модулей. Файлы файловой группы, оптимизированные для памяти, теперь можно хранить, помещать в резервную копию и восстанавливать с помощью службы хранилища Azure. (CTP 1.0)
- **DATABASE SCOPED CREDENTIAL** — новый класс защищаемых элементов, поддерживающих разрешения CONTROL, ALTER, REFERENCES, TAKE OWNERSHIP и VIEW DEFINITION. ADMINISTER DATABASE BULK OPERATIONS теперь отображается в sys.fn_builtin_permissions. (CTP 1.0)
- Добавлена база данных **COMPATIBILITY_LEVEL 140**. (CTP 1.0).  

Дополнительные сведения см. в разделе [What's new in SQL Server 2017 Database Engine](~/database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md) (Новые возможности ядра СУБД SQL Server 2017).

## <a name="sql-server-2017-integration-services-ssis"></a>Службы SQL Server 2017 Integration Services (SSIS)
- Новый компонент **Scale Out** в SSIS содержит следующие новые и измененные функции. Дополнительные сведения см. в разделе [What's New in Integration Services in SQL Server 2017](~/integration-services/what-s-new-in-integration-services-in-sql-server-2017.md) (Новые возможности Integration Services в SQL Server 2017). (RC1)
    -   Мастер масштабирования Scale Out теперь поддерживает высокий уровень доступности.
    -   Улучшена отработка отказа для журналов выполнения из рабочих ролей масштабирования Scale Out.
    -   Параметр *runincluster* хранимой процедуры **[catalog].[create_execution]** переименован в *runinscaleout* для согласованности и удобства чтения.
    -   Каталог SSIS содержит новое глобальное свойство, позволяющее указать режим по умолчанию для выполнения SSIS-пакетов.
- В новом компоненте **Scale Out для SSIS** вы теперь можете использовать параметр **Use32BitRuntime** при активации выполнения. (CTP 2.1)
- SQL Server 2017 Integration Services (SSIS) теперь поддерживает **SQL Server на Linux**, и новый пакет позволяет вам запускать пакеты SSIS в Linux из командной строки. Подробнее см. в [записи блога с объявлением о поддержке SSIS для Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/). (CTP 2.1)
- Новый компонент **Scale Out для SSIS** значительно упрощает запуск SSIS на множестве компьютеров. См. раздел [Integration Services Scale Out](~/integration-services/scale-out/integration-services-ssis-scale-out.md). (CTP 1.0)
- Источник OData и диспетчер подключений OData теперь поддерживают подключение к веб-каналам OData в Microsoft Dynamics AX Online и Microsoft Dynamics CRM Online. (CTP 1.0)

Дополнительные сведения см. в разделе [What's New in Integration Services in SQL Server 2017](~/integration-services/what-s-new-in-integration-services-in-sql-server-2017.md) (Новые возможности Integration Services в SQL Server 2017).

## <a name="sql-server-2017-master-data-services-mds"></a>Службы SQL Server 2017 Master Data Services (MDS)
- Обновление с SQL Server 2012, SQL Server 2014 или SQL Server 2016 до SQL Server 2017 Master Data Services обеспечит вам улучшенную производительность и усовершенствованный интерфейс. 
- Теперь вы можете просматривать на странице **Обозреватель** веб-приложения отсортированный список сущностей, коллекций и иерархий.
- Использование хранимой процедуры позволило значительно ускорить промежуточную обработку миллионов записей.
- Кроме того, улучшена работа при разворачивании на странице **Управление группами** папки **Сущности** для назначения моделям разрешений. Страница **Управление группами** находится в веб-приложении в разделе **Безопасность**. Дополнительные сведения об улучшении производительности см. в разделе [https://support.microsoft.com/help/4023865?preview](https://support.microsoft.com/help/4023865?preview). Дополнительные сведения о назначении разрешений: [Назначение разрешения для объекта модели (службы Master Data Services)](../master-data-services/assign-model-object-permissions-master-data-services.md).

## <a name="sql-server-2017-analysis-services-ssas"></a>Службы SQL Server 2017 Analysis Services (SSAS) 
SQL Server Analysis Services 2017 включает множество улучшений для табличных моделей. К ним относятся следующие объекты.
- Табличный режим стал параметром установки по умолчанию для Analysis Services. (CTP 2.0)
- Безопасность на уровне объектов для защиты метаданных табличных моделей. (CTP 2.0)
- Возможность легко создавать связи на основе полей дат. (CTP 2.0)
- Новые источники **получения данных** (Power Query) и поддержка существующих источников данных DirectQuery для запросов на языке M. (CTP 2.0) 
- Редактор DAX для SSDT. (CTP 2.0)
- Подсказки по кодированию — продвинутая функция для оптимизации обновления данных больших табличных моделей в памяти. (CTP 1.3)
- Поддержка **уровня совместимости 1400** для табличных моделей. Чтобы создать новый проект табличной модели с уровнем совместимости 1400 или перевести уже существующий проект на этот уровень, загрузите и установите [SQL Server Data Tools (SSDT) 17.0 RC2](https://go.microsoft.com/fwlink?LinkId=837939). (CTP 1.1)
- Современный интерфейс **получения данных** для табличных моделей с уровнем совместимости 1400. См. [блог команды разработчиков Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2016/12/16/introducing-a-modern-get-data-experience-for-sql-server-vnext-on-windows-ctp-1-1-for-analysis-services/). (CTP 1.1)
- Свойство **Скрыть члены** скрывает пустые элементы в неоднородных иерархиях. (CTP 1.1)
- Новое действие **Строки детализации** для конечного пользователя, позволяющее **Показать подробности** по статистических данным. Функции [SELECTCOLUMNS](/dax/selectcolumns-function-dax) и **DETAILROWS** для создания выражений со строками детализации. (CTP 1.1)
- DAX-оператор **IN** для указания множества значений. (CTP 1.1)

Дополнительные сведения см. в статье [What's New in SQL Server Analysis Services](/analysis-services/what-s-new-in-analysis-services) (Новые возможности SQL Server Analysis Services).

## <a name="sql-server-2017-reporting-services-ssrs"></a>Службы SQL Server 2017 Reporting Services (SSRS)
Службы SQL Server Reporting Services больше не доступны для установки с помощью программы установки SQL Server. Перейдите в Центр загрузки Майкрософт, чтобы [загрузить службы Microsoft SQL Server 2017 Reporting Services](https://www.microsoft.com/download/details.aspx?id=55252). 
- В отчетах теперь доступны комментарии, позволяющие сообщать свою точку зрения и взаимодействовать с другими пользователями. Для комментариев также доступны вложения.
- В последних выпусках построителя отчетов и SQL Server Data Tools вы можете создавать собственные запросы DAX для поддерживаемых табличных моделей данных SQL Server Analysis Services, перетаскивая нужные поля в конструкторах запросов. См. [блог по Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/2017/03/09/query-designer-support-for-dax-now-available-in-report-builder-and-sql-server-data-tools/).
- В целях разработки и настройки современных приложений службы SSRS теперь поддерживают API RESTful, полностью совместимый с OpenAPI. Полная спецификация и документация по API теперь находится на сайте [swaggerhub](https://app.swaggerhub.com/apis/microsoft-rs/SSRS/2.0).

Дополнительные сведения см. в разделе [What's new in SQL Server Reporting Services (SSRS)](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md) (Новые возможности служб SQL Server Reporting Services (SSRS)).

## <a name="machine-learning-in-sql-server-2017"></a>Машинное обучение в SQL Server 2017 

Службы R в SQL Server были переименованы в **Службы машинного обучения SQL Server**, чтобы отразить появление поддержки Python в дополнение к языку R. Вы можете использовать службы машинного обучения (в базе данных) для запуска сценариев R или Python в SQL Server либо установить **сервер машинного обучения Майкрософт (автономный)** для развертывания и использования моделей R и Python, не требующих SQL Server. 

Разработчикам в SQL Server теперь доступны обширные библиотеки машинного обучения и искусственного интеллекта для Python в экосистеме открытого кода, а также последние инновации от Майкрософт.

- **revoscalepy** — этот эквивалент RevoScaleR (Python) включает параллельные алгоритмы для линейных и логистических регрессий, деревьев решений, усиленных деревьев и случайных лесов, а также обширный набор API для преобразования и перемещения данных, контекстов удаленного вычисления и источников данных.
- **microsoftml** — этот современный пакет алгоритмов и преобразований для машинного обучения с привязками Python включает инструменты работы с глубокими нейронными сетями, быстрыми деревьями и лесами принятия решений, а также оптимизированные алгоритмы линейной и логистической регрессии. Вы также получите предварительно обученные модели на основе моделей ResNet, которые можно использовать для извлечения образов или анализа мнений.
- **Практическое использование Python с T-SQL** — простое развертывание кода Python с помощью хранимой процедуры `sp_execute_external_script`. Достигните отличной производительности, используя потоковую передачу данных из процессов SQL в процессы Python и параллелизацию кольца MPI.
- **Python в контекстах вычислений SQL Server** — исследователи данных и разработчики могут выполнять код Python удаленно из своей среды разработки для исследования данных и разработки моделей без перемещения данных.
- **Собственная оценка** — функция PREDICT в Transact-SQL, которую можно использовать для выполнения оценки в любом экземпляре SQL Server 2017, даже если язык R не установлен. Требуется только обучить модель с помощью одного из поддерживаемых алгоритмов RevoScaleR и revoscalepy, а затем сохранить модель в новом компактном двоичном формате.
- **Управление пакетами** — T-SQL теперь поддерживает оператор CREATE EXTERNAL LIBRARY, который предоставляет администраторам баз данных больше возможностей для управления с помощью пакетов R. Используйте роли для управления доступом к частным и общим пакетам, хранения пакетов R в базе данных и предоставления пользователям общего доступа к ним.
- **Повышение производительности** — хранимая процедура `sp_execute_external_script` оптимизирована для поддержки выполнения пакетных операций для данных columnstore.


Дополнительные сведения см. в разделе [What's new in SQL Server Machine Learning Services](~/advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md) (Новые возможности служб машинного обучения SQL Server).

## <a name="next-steps"></a>Следующие шаги
- Ознакомьтесь с [заметками о выпуске SQL Server 2017](sql-server-2017-release-notes.md).
- [Новые возможности SQL Server 2017 на Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-whats-new).
- Узнайте, [что нового в SQL Server 2016](what-s-new-in-sql-server-2016.md).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
