---
title: "Использование динамических административных представлений для мониторинга служб Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22b82b2d-867f-4ebf-9288-79d1cdd62f18
caps.latest.revision: 16
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 16
---
# Использование динамических административных представлений для мониторинга служб Analysis Services
  Динамические административные представления служб Analysis Services — это структуры запросов, которые предоставляют сведения о локальных операциях сервера и его состоянии. Структура запроса — это интерфейс для наборов строк схемы, которые возвращают метаданные и сведения об экземпляре служб Analysis Services.  
  
 В большинстве запросов к динамическим административным представлениям используется инструкция **SELECT** и схема **$System** с набором строк схемы XML/A.  
  
```  
SELECT * FROM $System.<schemaRowset>  
```  
  
 Запросы к динамическим административным представлениям возвращают сведения о состоянии сервера, который является текущим на момент выполнения запроса. Для наблюдения за операциями в режиме реального времени воспользуйтесь трассировкой. Дополнительные сведения см. в статье [Use SQL Server Profiler to Monitor Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md).  
  
 Этот раздел включает следующие подразделы:  
  
 [Преимущества использования запросов к динамическим административным представлениям](#bkmk_ben)  
  
 [Примеры и сценарии](#bkmk_ex)  
  
 [Синтаксис запроса](#bkmk_syn)  
  
 [Средства и разрешения](#bkmk_tools)  
  
 [Справочник по DMV-интерфейсу](#bkmk_ref)  
  
##  <a name="bkmk_ben"></a> Преимущества использования запросов к динамическим административным представлениям  
 Запросы к динамическим административным представлениям возвращают сведения об операциях и использовании ресурсов, недоступные через другие средства.  
  
 Запросы к динамическим административным представлениям являются альтернативой запуску команд XML/A. Для большинства администраторов написание запроса к динамическому административному представлению проще, поскольку синтаксис этих запросов основан на SQL. Кроме того, результирующий набор возвращается в табличном формате, который легче читать и копировать.  
  
##  <a name="bkmk_ex"></a> Примеры и сценарии  
 Запрос к динамическому административному представлению позволяет ответить на вопросы об активных сеансах и соединениях и о том, какие объекты потребляют больше всего ресурсов ЦП или памяти в определенное время. В этом разделе приведены примеры сценариев, в которых обычно используются запросы к динамическим административным представлениям. Дополнительные сведения об использовании запросов к динамическим административным представлениям для мониторинга экземпляра сервера см. в [Руководстве по использованию служб Analysis Services SQL Server 2008 R2](http://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409) .  
  
 `Select * from $System.discover_object_activity` /** Этот запрос сообщает о деятельности объекта с момента последнего запуска службы. Примеры запросов к этому динамическому административному представлению см. в разделе [Создание объекта System.Discover_Object_Activity](http://go.microsoft.com/fwlink/?linkid=221322).  
  
 `Select * from $System.discover_object_memory_usage` /** Этот запрос сообщает о потреблении памяти объектом.  
  
 `Select * from $System.discover_sessions` /** Этот запрос сообщает об активных сеансах, включая сеанс пользователя и его длительность.  
  
 `Select * from $System.discover_locks` /** Этот запрос возвращает моментальный снимок блокировок, которые используются в определенный момент времени.  
  
##  <a name="bkmk_syn"></a> Синтаксис запроса  
 Обработчик запросов к динамическим административным представлениям в обработчике интеллектуального анализа данных. Синтаксис запросов к динамическим административным представлениям основан на инструкции [SELECT (расширения интеллектуального анализа данных)](../../dmx/select-dmx.md).  
  
 Несмотря на то, что синтаксис запросов к динамическим административным представлениям основывается на инструкции SQL SELECT, он не поддерживает полный синтаксис инструкции SELECT. В частности, операторы JOIN, GROUP BY, LIKE, CAST и CONVERT не поддерживаются.  
  
```  
SELECT [DISTINCT] [TOP <n>] <select list>  
FROM $System.<schemaRowset>  
[WHERE <condition expression>]  
[ORDER BY <expression>[DESC|ASC]]  
```  
  
 Следующий пример для DISCOVER_CALC_DEPENDENCY иллюстрирует использование оператора WHERE для передачи параметра в запрос.  
  
```  
SELECT * FROM $System.DISCOVER_CALC_DEPENDENCY  
WHERE OBJECT_TYPE = 'ACTIVE_RELATIONSHIP'  
```  
  
 Также для наборов строк схемы с ограничениями запрос должен включать функцию SYSTEMRESTRICTSCHEMA. В следующем примере возвращаются метаданные языка CSDL о табличных моделях, запущенных на сервере в табличном режиме. Обратите внимание, что CATALOG_NAME вводится с учетом регистра.  
  
```  
Select * from SYSTEMRESTRICTSCHEMA ($System.Discover_csdl_metadata, [CATALOG_NAME] = 'Adventure Works DW')  
```  
  
##  <a name="bkmk_tools"></a> Средства и разрешения  
 Для выполнения запроса к динамическому административному представлению на экземпляре служб Analysis Services нужно обладать правами системного администратора.  
  
 Можно использовать любое клиентское приложение, поддерживающее многомерные или DMX-запросы, включая среду SQL Server Management Studio, отчет служб Reporting Services или панель мониторинга PerformancePoint.  
  
 Для выполнения запроса к динамическому административному представлению из среды Management Studio подключитесь к нужному экземпляру и нажмите кнопку **Создать запрос**. Можно выполнить запрос из окна создания многомерных или DMX-запросов.  
  
##  <a name="bkmk_ref"></a> Справочник по DMV-интерфейсу  
 Не у всех наборов строк схемы есть интерфейс динамических административных представлений. Чтобы получить список всех наборов строк схемы, к которым можно выполнять запросы с помощью динамических административных представлений, выполните следующий запрос.  
  
```  
SELECT * FROM $System.DBSchema_Tables   
WHERE TABLE_TYPE = 'SCHEMA'   
ORDER BY TABLE_NAME ASC  
```  
  
> [!NOTE]  
>  Если динамическое административное представление недоступно для определенного набора строк, сервер возвращает следующую ошибку: "Тип запроса "\<набор_строк_схемы>" не распознан сервером". Все остальные ошибки указывают на проблемы с синтаксисом.  
  
|Набор строк|Description|  
|------------|-----------------|  
|[Набор строк DBSCHEMA_CATALOGS](../../analysis-services/schema-rowsets/ole-db/dbschema-catalogs-rowset.md)|Возвращает список баз данных служб Analysis Services для текущего соединения.|  
|[Набор строк DBSCHEMA_COLUMNS](../../analysis-services/schema-rowsets/ole-db/dbschema-columns-rowset.md)|Возвращает список всех столбцов в текущей базе данных. Этот список можно использовать для построения запроса к динамическому административному представлению.|  
|[Набор строк DBSCHEMA_PROVIDER_TYPES](../../analysis-services/schema-rowsets/ole-db/dbschema-provider-types-rowset.md)|Возвращает сведения о базовых типах данных, поддерживаемых поставщиком данных OLE DB.|  
|[Набор строк DBSCHEMA_TABLES](../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md)|Возвращает список всех таблиц в текущей базе данных. Этот список можно использовать для построения запроса к динамическому административному представлению.|  
|[Набор строк DISCOVER_CALC_DEPENDENCY](../../analysis-services/schema-rowsets/xml/discover-calc-dependency-rowset.md)|Возвращает список столбцов и таблиц, используемых в модели, имеющей зависимости с другими столбцами и таблицами.|  
|[Набор строк DISCOVER_COMMAND_OBJECTS](../../analysis-services/schema-rowsets/xml/discover-command-objects-rowset.md)|Предоставляет сведения по использованию ресурсов и активности для объектов, которые используются указанной командой.|  
|[Набор строк DISCOVER_COMMANDS](../../analysis-services/schema-rowsets/xml/discover-commands-rowset.md)|Предоставляет сведения по использованию ресурсов и активности для текущей исполняемой команды.|  
|[Набор строк DISCOVER_CONNECTIONS](../../analysis-services/schema-rowsets/xml/discover-connections-rowset.md)|Предоставляет сведения об использовании ресурсов и активности для открытых соединений со службами Analysis Services.|  
|[Набор строк DISCOVER_CSDL_METADATA](../../analysis-services/schema-rowsets/xml/discover-csdl-metadata-rowset.md)|Возвращает сведения о табличной модели.<br /><br /> Необходимо добавить функцию SYSTEMRESTRICTSCHEMA и дополнительные параметры.|  
|[Набор строк DISCOVER_DB_CONNECTIONS](../../analysis-services/schema-rowsets/xml/discover-db-connections-rowset.md)|Предоставляет сведения об использовании ресурсов и активности для открытых соединений со службами Analysis Services к внешним источникам данных, например, во время обработки или импорта.|  
|[Набор строк DISCOVER_DIMENSION_STAT](../../analysis-services/schema-rowsets/xml/discover-dimension-stat-rowset.md)|Возвращает атрибуты в измерении или столбцы в таблице, в зависимости от типа модели.|  
|[Набор строк DISCOVER_ENUMERATORS](../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)|Возвращает метаданные о перечислителях, поддерживаемых для конкретных источников данных.|  
|[Набор строк DISCOVER_INSTANCES](../../analysis-services/schema-rowsets/ole-db-olap/discover-instances-rowset.md)|Возвращает сведения об указанном экземпляре.<br /><br /> Необходимо добавить функцию SYSTEMRESTRICTSCHEMA и дополнительные параметры.|  
|[Набор строк DISCOVER_JOBS](../../analysis-services/schema-rowsets/xml/discover-jobs-rowset.md)|Возвращает сведения о текущих заданиях.|  
|[Набор строк DISCOVER_KEYWORDS (XMLA)](../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)|Возвращает список зарезервированных ключевых слов.|  
|[Набор строк DISCOVER_LITERALS](../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)|Возвращает список литералов, включая типы данных и значения, поддерживаемые XML для аналитики.|  
|[Набор строк DISCOVER_LOCKS](../../analysis-services/schema-rowsets/xml/discover-locks-rowset.md)|Возвращает моментальный снимок блокировок, используемых в указанное время.|  
|[Набор строк DISCOVER_MEMORYGRANT](../../analysis-services/schema-rowsets/xml/discover-memorygrant-rowset.md)|Возвращает сведения о памяти, выделенной службами Analysis Services при запуске.|  
|[Набор строк DISCOVER_MEMORYUSAGE](../../analysis-services/schema-rowsets/xml/discover-memoryusage-rowset.md)|Показывает использование памяти определенными объектами.|  
|[Набор строк DISCOVER_OBJECT_ACTIVITY](../../analysis-services/schema-rowsets/xml/discover-object-activity-rowset.md)|Сообщает об активности объекта с момента последнего запуска службы.|  
|[Набор строк DISCOVER_OBJECT_MEMORY_USAGE](../../analysis-services/schema-rowsets/xml/discover-object-memory-usage-rowset.md)|Сообщает об использовании памяти объектом.|  
|[Набор рядов DISCOVER_PARTITION_DIMENSION_STAT](../../analysis-services/schema-rowsets/xml/discover-partition-dimension-stat-rowset.md)|Предоставляет сведения об атрибутах в измерении.<br /><br /> Необходимо добавить функцию SYSTEMRESTRICTSCHEMA и дополнительные параметры.|  
|[Набор строк DISCOVER_PARTITION_STAT](../../analysis-services/schema-rowsets/xml/discover-partition-stat-rowset.md)|Предоставляет сведения о секциях в измерении, таблице или группе мер.<br /><br /> Необходимо добавить функцию SYSTEMRESTRICTSCHEMA и дополнительные параметры.|  
|[Набор строк DISCOVER_PERFORMANCE_COUNTERS](../../analysis-services/schema-rowsets/xml/discover-performance-counters-rowset.md)|Список столбцов, используемых счетчиком производительности.<br /><br /> Необходимо добавить функцию SYSTEMRESTRICTSCHEMA и дополнительные параметры.|  
|[Набор строк DISCOVER_PROPERTIES](../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md)|Возвращает сведения о свойствах, поддерживаемых XML для аналитики для указанного источника данных.|  
|[Набор строк DISCOVER_SCHEMA_ROWSETS](../../analysis-services/schema-rowsets/xml/discover-schema-rowsets-rowset.md)|Возвращает имена, ограничения, описание и другие сведения для всех значений перечисления, поддерживаемых XML для аналитики.|  
|[Набор строк DISCOVER_SESSIONS](../../analysis-services/schema-rowsets/xml/discover-sessions-rowset.md)|Сообщает об активных сеансах, включая сеанс пользователя и его длительность.|  
|[Набор строк DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS](../../analysis-services/schema-rowsets/xml/discover-storage-table-column-segments-rowset.md)|Содержит сведения на уровне столбцов и сегментов о таблицах хранилища, используемых в базе данных служб Analysis Services в табличном режиме или режиме SharePoint.|  
|[Набор строк DISCOVER_STORAGE_TABLE_COLUMNS](../../analysis-services/schema-rowsets/xml/discover-storage-table-columns-rowset.md)|Позволяет клиенту определить назначение столбцов таблиц хранилища, используемых базой данных служб Analysis Services, работающей в табличном режиме или режиме SharePoint.|  
|[Набор строк DISCOVER_STORAGE_TABLES](../../analysis-services/schema-rowsets/xml/discover-storage-tables-rowset.md)|Возвращает сведения о таблицах, используемых для хранения моделей в базе данных табличной модели.|  
|[Набор строк DISCOVER_TRACE_COLUMNS](../../analysis-services/schema-rowsets/xml/discover-trace-columns-rowset.md)|Возвращает XML-описание столбцов, доступных в трассировке.|  
|[Набор строк DISCOVER_TRACE_DEFINITION_PROVIDERINFO](../../analysis-services/schema-rowsets/xml/discover-trace-definition-providerinfo-rowset.md)|Возвращает сведения об имени и версии поставщика.|  
|[Набор строк DISCOVER_TRACE_EVENT_CATEGORIES](../../analysis-services/schema-rowsets/xml/discover-trace-event-categories-rowset.md)|Возвращает список доступных категорий.|  
|[Набор строк DISCOVER_TRACES](../../analysis-services/schema-rowsets/xml/discover-traces-rowset.md)|Возвращает список трассировок, работающих в данном соединении.|  
|[Набор строк DISCOVER_TRANSACTIONS](../../analysis-services/schema-rowsets/xml/discover-transactions-rowset.md)|Возвращает список транзакций, работающих в данном соединении.|  
|[Набор строк DISCOVER_XEVENT_TRACE_DEFINITION](../Topic/DISCOVER_XEVENT_TRACE_DEFINITION%20Rowset.md)|Возвращает список трассировок xevent, работающих в данном соединении.|  
|[Набор строк DMSCHEMA_MINING_COLUMNS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|Список отдельных столбцов всех моделей интеллектуального анализа данных, доступных в текущем соединении.|  
|[Набор строк DMSCHEMA_MINING_FUNCTIONS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)|Возвращает список функций, поддерживаемых алгоритмами интеллектуального анализа данных на сервере.|  
|[Набор строк DMSCHEMA_MINING_MODEL_CONTENT](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|Возвращает набор строк, состоящий из столбцов, описывающий текущую модель.|  
|[Набор строк DMSCHEMA_MINING_MODEL_CONTENT_PMML](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)|Возвращает набор строк, состоящий из столбцов, описывающий текущую модель в формате PMML.|  
|[Набор строк DMSCHEMA_MINING_MODEL_XML](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)|Возвращает набор строк, состоящий из столбцов, описывающий текущую модель в формате PMML.|  
|[Набор строк DMSCHEMA_MINING_MODELS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|Возвращает список моделей интеллектуального анализа данных в текущей базе данных.|  
|[Набор строк DMSCHEMA_MINING_SERVICE_PARAMETERS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|Возвращает список параметров для алгоритмов на сервере.|  
|[Набор строк DMSCHEMA_MINING_SERVICES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|Предоставляет список алгоритмов интеллектуального анализа данных, доступных на сервере.|  
|[Набор строк DMSCHEMA_MINING_STRUCTURE_COLUMNS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|Возвращает список всех столбцов всех моделей интеллектуального анализа данных, доступных в текущем соединении.|  
|[Набор строк DMSCHEMA_MINING_STRUCTURES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|Список структур интеллектуального анализа данных, доступных в текущем соединении.|  
|[Набор строк MDSCHEMA_CUBES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-cubes-rowset.md)|Возвращает сведения о кубах, определенных в текущей базе данных.|  
|[Набор строк MDSCHEMA_DIMENSIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset.md)|Возвращает сведения об измерениях, определенных в текущей базе данных.|  
|[Набор строк MDSCHEMA_FUNCTIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-functions-rowset.md)|Возвращает список функций, доступных клиентским приложениям, подключенным к базе данных.|  
|[Набор строк MDSCHEMA_HIERARCHIES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)|Возвращает сведения об иерархиях, определенных в текущей базе данных.|  
|[Набор строк MDSCHEMA_INPUT_DATASOURCES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)|Возвращает сведения об исходных объектах данных, определенных в текущей базе данных.|  
|[Набор строк MDSCHEMA_KPIS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-kpis-rowset.md)|Возвращает сведения о ключевых показателях эффективности, определенных в текущей базе данных.|  
|[Набор строк MDSCHEMA_LEVELS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-levels-rowset.md)|Возвращает сведения об уровнях в иерархиях, определенных в текущей базе данных.|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS, набор строк](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md)|Список измерений групп мер.|  
|[Набор строк MDSCHEMA_MEASUREGROUPS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset.md)|Возвращает список групп мер в текущем соединении.|  
|[Набор строк MDSCHEMA_MEASURES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measures-rowset.md)|Возвращает список мер в текущем соединении.|  
|[Набор строк MDSCHEMA_MEMBERS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-members-rowset.md)|Возвращает список всех элементов в текущем соединении по базе данных, кубу и измерению.|  
|[Набор строк MDSCHEMA_PROPERTIES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)|Возвращает полное имя каждого свойства, включая тип свойства, тип данных и другие метаданные.|  
|[MDSCHEMA_SETS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-sets-rowset.md)|Возвращает список наборов, определенных в текущем соединении.|  
  
## См. также раздел  
 [Руководство по использованию служб SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409)   
 [Новый System.Discover_Object_Activity](http://go.microsoft.com/fwlink/?linkid=221322)   
 [Новая функция SYSTEMRESTRICTEDSCHEMA для ограниченных наборов строк и динамических административных представлений](http://go.microsoft.com/fwlink/?LinkId=231885)  
  
  