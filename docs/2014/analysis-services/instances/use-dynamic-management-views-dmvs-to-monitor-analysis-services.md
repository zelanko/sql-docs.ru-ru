---
title: Использование динамических административных представлений (DMV) для мониторинга Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 22b82b2d-867f-4ebf-9288-79d1cdd62f18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a02d8d5b113e4773aa7cdfbbf20975fd70218e1a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66079574"
---
# <a name="use-dynamic-management-views-dmvs-to-monitor-analysis-services"></a>Использование динамических административных представлений для мониторинга служб Analysis Services
  Динамические административные представления служб Analysis Services — это структуры запросов, которые предоставляют сведения о локальных операциях сервера и его состоянии. Структура запроса — это интерфейс для наборов строк схемы, которые возвращают метаданные и сведения об экземпляре служб Analysis Services.  
  
 В большинстве запросов к динамическим административным представлениям используется инструкция `SELECT` и схема `$System` с набором строк схемы XML/A.  
  
```  
SELECT * FROM $System.<schemaRowset>  
```  
  
 Запросы к динамическим административным представлениям возвращают сведения о состоянии сервера, который является текущим на момент выполнения запроса. Для наблюдения за операциями в режиме реального времени воспользуйтесь трассировкой. Дополнительные сведения см. в статье [Use SQL Server Profiler to Monitor Analysis Services](use-sql-server-profiler-to-monitor-analysis-services.md).  
  
 Этот раздел включает следующие подразделы:  
  
 [Преимущества использования запросов динамического административного представления](#bkmk_ben)  
  
 [Примеры и сценарии](#bkmk_ex)  
  
 [Синтаксис запроса](#bkmk_syn)  
  
 [Средства и разрешения](#bkmk_tools)  
  
 [Ссылка на динамическое административное представление](#bkmk_ref)  
  
##  <a name="bkmk_ben"></a>Преимущества использования запросов динамического административного представления  
 Запросы к динамическим административным представлениям возвращают сведения об операциях и использовании ресурсов, недоступные через другие средства.  
  
 Запросы к динамическим административным представлениям являются альтернативой запуску команд XML/A. Для большинства администраторов написание запроса к динамическому административному представлению проще, поскольку синтаксис этих запросов основан на SQL. Кроме того, результирующий набор возвращается в табличном формате, который легче читать и копировать.  
  
##  <a name="bkmk_ex"></a>Примеры и сценарии  
 Запрос к динамическому административному представлению позволяет ответить на вопросы об активных сеансах и соединениях и о том, какие объекты потребляют больше всего ресурсов ЦП или памяти в определенное время. В этом разделе приведены примеры сценариев, в которых обычно используются запросы к динамическим административным представлениям. Дополнительные сведения об использовании запросов к динамическим административным представлениям для мониторинга экземпляра сервера см. в [Руководстве по использованию служб Analysis Services SQL Server 2008 R2](https://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409) .  
  
 
  `Select * from $System.discover_object_activity` /** Этот запрос сообщает о деятельности объекта с момента последнего запуска службы. Примеры запросов к этому динамическому административному представлению см. в разделе [Создание объекта System.Discover_Object_Activity](https://go.microsoft.com/fwlink/?linkid=221322).  
  
 
  `Select * from $System.discover_object_memory_usage` /** Этот запрос сообщает о потреблении памяти объектом.  
  
 
  `Select * from $System.discover_sessions` /** Этот запрос сообщает об активных сеансах, включая сеанс пользователя и его длительность.  
  
 
  `Select * from $System.discover_locks` /** Этот запрос возвращает моментальный снимок блокировок, которые используются в определенный момент времени.  
  
##  <a name="bkmk_syn"></a>Синтаксис запроса  
 Обработчик запросов к динамическим административным представлениям в обработчике интеллектуального анализа данных. Синтаксис запросов к динамическим административным представлениям основан на инструкции [SELECT (расширения интеллектуального анализа данных)](/sql/dmx/select-dmx).  
  
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
  
##  <a name="bkmk_tools"></a>Средства и разрешения  
 Для выполнения запроса к динамическому административному представлению на экземпляре служб Analysis Services нужно обладать правами системного администратора.  
  
 Можно использовать любое клиентское приложение, поддерживающее многомерные или DMX-запросы, включая среду SQL Server Management Studio, отчет служб Reporting Services или панель мониторинга PerformancePoint.  
  
 Для выполнения запроса к динамическому административному представлению из среды Management Studio подключитесь к нужному экземпляру и нажмите кнопку **Создать запрос**. Можно выполнить запрос из окна создания многомерных или DMX-запросов.  
  
##  <a name="bkmk_ref"></a>Ссылка на динамическое административное представление  
 Не у всех наборов строк схемы есть интерфейс динамических административных представлений. Чтобы получить список всех наборов строк схемы, к которым можно выполнять запросы с помощью динамических административных представлений, выполните следующий запрос.  
  
```  
SELECT * FROM $System.DBSchema_Tables   
WHERE TABLE_TYPE = 'SCHEMA'   
ORDER BY TABLE_NAME ASC  
```  
  
> [!NOTE]  
>  Если динамическое административное представление недоступно для данного набора строк, сервер возвращает следующую ошибку: " \<тип запроса счемаровсет> не распознан сервером". Все остальные ошибки указывают на проблемы с синтаксисом.  
  
|Набор строк|Description|  
|------------|-----------------|  
|[DBSCHEMA_CATALOGS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db/dbschema-catalogs-rowset)|Возвращает список баз данных служб Analysis Services для текущего соединения.|  
|[DBSCHEMA_COLUMNS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db/dbschema-columns-rowset)|Возвращает список всех столбцов в текущей базе данных. Этот список можно использовать для построения запроса к динамическому административному представлению.|  
|[DBSCHEMA_PROVIDER_TYPES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db/dbschema-provider-types-rowset)|Возвращает сведения о базовых типах данных, поддерживаемых поставщиком данных OLE DB.|  
|[DBSCHEMA_TABLES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db/dbschema-tables-rowset)|Возвращает список всех таблиц в текущей базе данных. Этот список можно использовать для построения запроса к динамическому административному представлению.|  
|[DISCOVER_CALC_DEPENDENCY набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-calc-dependency-rowset)|Возвращает список столбцов и таблиц, используемых в модели, имеющей зависимости с другими столбцами и таблицами.|  
|[DISCOVER_COMMAND_OBJECTS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-command-objects-rowset)|Предоставляет сведения по использованию ресурсов и активности для объектов, которые используются указанной командой.|  
|[DISCOVER_COMMANDS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-commands-rowset)|Предоставляет сведения по использованию ресурсов и активности для текущей исполняемой команды.|  
|[DISCOVER_CONNECTIONS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-connections-rowset)|Предоставляет сведения об использовании ресурсов и активности для открытых соединений со службами Analysis Services.|  
|[DISCOVER_CSDL_METADATA набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset)|Возвращает сведения о табличной модели.<br /><br /> Необходимо добавить функцию SYSTEMRESTRICTSCHEMA и дополнительные параметры.|  
|[DISCOVER_DB_CONNECTIONS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-db-connections-rowset)|Предоставляет сведения об использовании ресурсов и активности для открытых соединений со службами Analysis Services к внешним источникам данных, например, во время обработки или импорта.|  
|[DISCOVER_DIMENSION_STAT набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-dimension-stat-rowset)|Возвращает атрибуты в измерении или столбцы в таблице, в зависимости от типа модели.|  
|[DISCOVER_ENUMERATORS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-enumerators-rowset)|Возвращает метаданные о перечислителях, поддерживаемых для конкретных источников данных.|  
|[DISCOVER_INSTANCES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/discover-instances-rowset)|Возвращает сведения об указанном экземпляре.<br /><br /> Необходимо добавить функцию SYSTEMRESTRICTSCHEMA и дополнительные параметры.|  
|[DISCOVER_JOBS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-jobs-rowset)|Возвращает сведения о текущих заданиях.|  
|[DISCOVER_KEYWORDS набор строк &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-keywords-rowset-xmla)|Возвращает список зарезервированных ключевых слов.|  
|[DISCOVER_LITERALS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-literals-rowset)|Возвращает список литералов, включая типы данных и значения, поддерживаемые XML для аналитики.|  
|[DISCOVER_LOCKS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-locks-rowset)|Возвращает моментальный снимок блокировок, используемых в указанное время.|  
|[DISCOVER_MEMORYGRANT набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-memorygrant-rowset)|Возвращает сведения о памяти, выделенной службами Analysis Services при запуске.|  
|[DISCOVER_MEMORYUSAGE набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-memoryusage-rowset)|Показывает использование памяти определенными объектами.|  
|[DISCOVER_OBJECT_ACTIVITY набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-object-activity-rowset)|Сообщает об активности объекта с момента последнего запуска службы.|  
|[DISCOVER_OBJECT_MEMORY_USAGE набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-object-memory-usage-rowset)|Сообщает об использовании памяти объектом.|  
|[DISCOVER_PARTITION_DIMENSION_STAT набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-partition-dimension-stat-rowset)|Предоставляет сведения об атрибутах в измерении.<br /><br /> Необходимо добавить функцию SYSTEMRESTRICTSCHEMA и дополнительные параметры.|  
|[DISCOVER_PARTITION_STAT набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-partition-stat-rowset)|Предоставляет сведения о секциях в измерении, таблице или группе мер.<br /><br /> Необходимо добавить функцию SYSTEMRESTRICTSCHEMA и дополнительные параметры.|  
|[DISCOVER_PERFORMANCE_COUNTERS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-performance-counters-rowset)|Список столбцов, используемых счетчиком производительности.<br /><br /> Необходимо добавить функцию SYSTEMRESTRICTSCHEMA и дополнительные параметры.|  
|[DISCOVER_PROPERTIES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-properties-rowset)|Возвращает сведения о свойствах, поддерживаемых XML для аналитики для указанного источника данных.|  
|[DISCOVER_SCHEMA_ROWSETS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-schema-rowsets-rowset)|Возвращает имена, ограничения, описание и другие сведения для всех значений перечисления, поддерживаемых XML для аналитики.|  
|[DISCOVER_SESSIONS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-sessions-rowset)|Сообщает об активных сеансах, включая сеанс пользователя и его длительность.|  
|[DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-storage-table-column-segments-rowset)|Содержит сведения на уровне столбцов и сегментов о таблицах хранилища, используемых в базе данных служб Analysis Services в табличном режиме или режиме SharePoint.|  
|[DISCOVER_STORAGE_TABLE_COLUMNS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-storage-table-columns-rowset)|Позволяет клиенту определить назначение столбцов таблиц хранилища, используемых базой данных служб Analysis Services, работающей в табличном режиме или режиме SharePoint.|  
|[DISCOVER_STORAGE_TABLES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-storage-tables-rowset)|Возвращает сведения о таблицах, используемых для хранения моделей в базе данных табличной модели.|  
|[DISCOVER_TRACE_COLUMNS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-trace-columns-rowset)|Возвращает XML-описание столбцов, доступных в трассировке.|  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-trace-definition-providerinfo-rowset)|Возвращает сведения об имени и версии поставщика.|  
|[DISCOVER_TRACE_EVENT_CATEGORIES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-trace-event-categories-rowset)|Возвращает список доступных категорий.|  
|[Набор строк DISCOVER_TRACES](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-traces-rowset)|Возвращает список трассировок, работающих в данном соединении.|  
|[DISCOVER_TRANSACTIONS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-transactions-rowset)|Возвращает список транзакций, работающих в данном соединении.|  
|[DISCOVER_XEVENT_TRACE_DEFINITION набор строк](../dev-guide/discover-xevent-trace-definition-rowset.md)|Возвращает список трассировок xevent, работающих в данном соединении.|  
|[DMSCHEMA_MINING_COLUMNS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-columns-rowset)|Список отдельных столбцов всех моделей интеллектуального анализа данных, доступных в текущем соединении.|  
|[Набор строк DMSCHEMA_MINING_FUNCTIONS](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-functions-rowset)|Возвращает список функций, поддерживаемых алгоритмами интеллектуального анализа данных на сервере.|  
|[DMSCHEMA_MINING_MODEL_CONTENT набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)|Возвращает набор строк, состоящий из столбцов, описывающий текущую модель.|  
|[DMSCHEMA_MINING_MODEL_CONTENT_PMML набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset)|Возвращает набор строк, состоящий из столбцов, описывающий текущую модель в формате PMML.|  
|[DMSCHEMA_MINING_MODEL_XML набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset)|Возвращает набор строк, состоящий из столбцов, описывающий текущую модель в формате PMML.|  
|[DMSCHEMA_MINING_MODELS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-models-rowset)|Возвращает список моделей интеллектуального анализа данных в текущей базе данных.|  
|[DMSCHEMA_MINING_SERVICE_PARAMETERS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset)|Возвращает список параметров для алгоритмов на сервере.|  
|[DMSCHEMA_MINING_SERVICES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)|Предоставляет список алгоритмов интеллектуального анализа данных, доступных на сервере.|  
|[DMSCHEMA_MINING_STRUCTURE_COLUMNS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset)|Возвращает список всех столбцов всех моделей интеллектуального анализа данных, доступных в текущем соединении.|  
|[DMSCHEMA_MINING_STRUCTURES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-structures-rowset)|Список структур интеллектуального анализа данных, доступных в текущем соединении.|  
|[MDSCHEMA_CUBES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-cubes-rowset)|Возвращает сведения о кубах, определенных в текущей базе данных.|  
|[MDSCHEMA_DIMENSIONS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset)|Возвращает сведения об измерениях, определенных в текущей базе данных.|  
|[MDSCHEMA_FUNCTIONS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-functions-rowset)|Возвращает список функций, доступных клиентским приложениям, подключенным к базе данных.|  
|[MDSCHEMA_HIERARCHIES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset)|Возвращает сведения об иерархиях, определенных в текущей базе данных.|  
|[MDSCHEMA_INPUT_DATASOURCES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset)|Возвращает сведения об исходных объектах данных, определенных в текущей базе данных.|  
|[MDSCHEMA_KPIS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-kpis-rowset)|Возвращает сведения о ключевых показателях эффективности, определенных в текущей базе данных.|  
|[MDSCHEMA_LEVELS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-levels-rowset)|Возвращает сведения об уровнях в иерархиях, определенных в текущей базе данных.|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset)|Список измерений групп мер.|  
|[Набор строк MDSCHEMA_MEASUREGROUPS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset)|Возвращает список групп мер в текущем соединении.|  
|[MDSCHEMA_MEASURES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-measures-rowset)|Возвращает список мер в текущем соединении.|  
|[MDSCHEMA_MEMBERS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-members-rowset)|Возвращает список всех элементов в текущем соединении по базе данных, кубу и измерению.|  
|[MDSCHEMA_PROPERTIES набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-properties-rowset)|Возвращает полное имя каждого свойства, включая тип свойства, тип данных и другие метаданные.|  
|[MDSCHEMA_SETS набор строк](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-sets-rowset)|Возвращает список наборов, определенных в текущем соединении.|  
  
## <a name="see-also"></a>См. также:  
 [Руководство по работе с SQL Server 2008 R2 Analysis Services](https://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409)   
 [Новый System. Discover_Object_Activity](https://go.microsoft.com/fwlink/?linkid=221322)   
 [Новая функция новая SYSTEMRESTRICTEDSCHEMA для ограниченных наборов строк и динамических административных представлений](https://go.microsoft.com/fwlink/?LinkId=231885)  
  
  
