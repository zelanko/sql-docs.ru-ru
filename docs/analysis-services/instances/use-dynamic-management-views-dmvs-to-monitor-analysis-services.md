---
title: Используйте динамические административные представления (DMV) в службах Analysis Services | Документация Майкрософт
ms.date: 09/25/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d59601d0706b65186ed5f260128c3c44a134d60e
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/10/2018
ms.locfileid: "48906404"
---
# <a name="dynamic-management-views-dmvs"></a>Динамические административные представления 

[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

Запросы, которые возвращают сведения о модели объектов, серверных операций и работоспособности сервера Analysis Services представлений динамического управления (DMV): Запрос, на основе SQL, представляет собой интерфейс для *наборы строк схемы*. Наборы строк схемы — predescribed таблиц, содержащих сведения об объектах служб Analysis Services и состоянии сервера, включая схему базы данных, активные сеансы, подключения, команды и заданий, которые выполняются на сервере.

Запросы к динамическим административным представлениям являются альтернативой запуску команд XML/A. Для большинства администраторов написание к Динамическому административному представлению проще, поскольку синтаксис основан на SQL Server. Кроме того результат возвращается в виде таблицы, который проще читать и копировать. 
  
Большинство динамического административного Представления запросы, использующие **ВЫБЕРИТЕ** инструкции и **$System** схемы с набором строк схемы XML/A, например:  
  
```  
SELECT * FROM $System.<schemaRowset>  
```  
  
 Запросы динамического административного Представления возвращают сведения о сервера и состояние объекта во время выполнения запроса. Для наблюдения за операциями в в режиме реального времени, используйте трассировкой. Дополнительные сведения о в режиме реального времени наблюдения с помощью трассировки, см. в разделе [использования SQL Server Profiler to Monitor Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md).  
  
## <a name="query-syntax"></a>синтаксис запроса

Обработчик запросов к динамическим административным представлениям в обработчике интеллектуального анализа данных. Синтаксис запросов к динамическим административным Представлениям основан на SELECT &#40;расширений интеллектуального анализа данных&#41; инструкции. Несмотря на то, что синтаксис запросов к динамическим административным представлениям основывается на инструкции SQL SELECT, он не поддерживает полный синтаксис инструкции SELECT. В частности, операторы JOIN, GROUP BY, LIKE, CAST и CONVERT не поддерживаются.  
  
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
  
Для наборов строк схемы, ограничениями запрос должен включать функцию SYSTEMRESTRICTSCHEMA. В следующем примере возвращается метаданные CSDL около 1103 табличной модели с уровнем совместимости. Обратите внимание, что CATALOG_NAME вводится с учетом регистра.  
  
```  
Select * from SYSTEMRESTRICTSCHEMA ($System.Discover_csdl_metadata, [CATALOG_NAME] = 'Adventure Works DW')  
```  

## <a name="examples-and-scenarios"></a>Примеры и сценарии

Запрос к динамическому административному представлению позволяет ответить на вопросы об активных сеансах и соединениях и о том, какие объекты потребляют больше всего ресурсов ЦП или памяти в определенное время. Пример:
  
 `Select * from $System.discover_object_activity`  
Этот запрос сообщает о деятельности объекта с момента последнего запуска службы. 
  
 `Select * from $System.discover_object_memory_usage`  
Этот запрос сообщает о потреблении памяти объектом.  
  
 `Select * from $System.discover_sessions`  
Этот запрос сообщает об активных сеансах, включая сеанс пользователя и его длительность.  
  
 `Select * from $System.discover_locks`   
Этот запрос возвращает моментальный снимок блокировок, которые используются в определенный момент времени.  


## <a name="tools-and-permissions"></a>Средства и разрешения

Можно использовать любое клиентское приложение, который поддерживает запросы многомерных Выражений или расширений интеллектуального анализа данных. В большинстве случаев лучше использовать SQL Server Management Studio. Необходимо иметь разрешения администратора сервера в экземпляре для запроса к динамическому административному Представлению.  
  
 **Для выполнения запроса к динамическим административным Представлениям из среды SQL Server Management Studio**

1. Подключитесь к серверу и объект модели, которые необходимо выполнить запрос. 
2. Щелкните правой кнопкой мыши объект сервера или базы данных > **новый запрос** > **многомерных Выражений**.
3. Введите запрос и нажмите кнопку **Execute**, или нажмите клавишу F5.
  
## <a name="schema-rowsets"></a>Наборы строк схемы

Не у всех наборов строк схемы есть интерфейс динамических административных представлений. Чтобы получить список всех наборов строк схемы, к которым можно выполнять запросы с помощью динамических административных представлений, выполните следующий запрос.  
 
```  
SELECT * FROM $System.DBSchema_Tables   
WHERE TABLE_TYPE = 'SCHEMA'   
ORDER BY TABLE_NAME ASC  
```  
  
Если динамическое административное Представление недоступно для определенного набора строк, сервер возвращает ошибку: `The <schemarowset> request type was not recognized by the server.` все остальные ошибки указывают на проблемы с синтаксисом.  

Наборы строк схемы, описанные в двух протоколов SQL Server Analysis Services:   

[[MS-SSAS-T]: SQL Server Analysis Services табличному протоколу](https://msdn.microsoft.com/library/mt719260) -описывает наборы строк схемы для табличных моделей на уровне совместимости 1200 и выше.

[[MS-SSAS]: протокол служб SQL Server Analysis](https://msdn.microsoft.com/library/ee320606) -описывает наборы строк схемы для многомерных и табличных моделей на уровни совместимости 1100 и 1103.

### <a name="rowsets-described-in-the-ms-ssas-t-sql-server-analysis-services-tabular-protocol"></a>Наборы строк, описано в [MS-SSAS-T]: SQL Server Analysis Services табличному протоколу

|Набор строк  |Описание  |
|---------|---------|
|[TMSCHEMA_ANNOTATIONS](https://msdn.microsoft.com/library/mt704370)|Сведения об объектах заметки в модели.|
|[TMSCHEMA_ATTRIBUTE_HIERARCHIES](https://msdn.microsoft.com/library/mt704362)     |   Сведения об объектах AttributeHierarchy для столбца.      |
|[TMSCHEMA_COLUMNS](https://msdn.microsoft.com/library/mt704373)    |  Сведения об объектах столбца в каждой таблице.       |
|[TMSCHEMA_COLUMN_PERMISSIONS](https://msdn.microsoft.com/library/mt842440)|Сведения об объектах ColumnPermission в каждой таблице разрешение.|
|[TMSCHEMA_CULTURES](https://msdn.microsoft.com/library/mt719125)|Сведения об объектах языка и региональных параметров в модели.|
|[TMSCHEMA_DATA_SOURCES](https://msdn.microsoft.com/library/mt719191)   |   Сведения об объектах источника данных в модели.      |
|[TMSCHEMA_DETAIL_ROWS_DEFINITIONS](https://msdn.microsoft.com/library/mt825017)|Сведения об объектах DetailRowsDefinition в модели.|
|[TMSCHEMA_EXPRESSIONS](https://msdn.microsoft.com/library/mt825015)|Сведения об объектах выражения в модели.|
|[TMSCHEMA_EXTENDED_PROPERTIES](https://msdn.microsoft.com/library/mt842451)|Сведения об объектах ExtendedProperty в модели.|
|[TMSCHEMA_HIERARCHIES](https://msdn.microsoft.com/library/mt719136)    |    Сведения об иерархии объектов в каждой таблице.     |
|[TMSCHEMA_KPIS](https://msdn.microsoft.com/library/mt719002)     |    Сведения об объектах ключевого показателя Эффективности в модели.     |
|[TMSCHEMA_LEVELS](https://msdn.microsoft.com/library/mt719038)     |   Сведения об объектах уровня в каждой иерархии.      |
|[TMSCHEMA_LINGUISTIC_METADATA](https://msdn.microsoft.com/library/mt719169)|Предоставляет сведения о синонимах для объектов в модели для конкретного языка и региональных параметров|
|[TMSCHEMA_MEASURES](https://msdn.microsoft.com/library/mt719218)     |    Сведения об объектах измерения в каждой таблице.     |
|[TMSCHEMA_MODEL](https://msdn.microsoft.com/library/mt719042)    |  Указывает объект модели в базе данных.       |
|[TMSCHEMA_OBJECT_TRANSLATIONS](https://msdn.microsoft.com/library/mt719119)|Предоставляет сведения о переводах различных объектов для языка и региональных параметров.|
|[TMSCHEMA_PARTITIONS](https://msdn.microsoft.com/library/mt704375)     |     Сведения об объектах секции в каждой таблице.    |
|[TMSCHEMA_PERSPECTIVE_COLUMNS](https://msdn.microsoft.com/library/mt719164)     |   Сведения об объектах PerspectiveColumn в каждом объекте PerspectiveTable.      |
|[TMSCHEMA_PERSPECTIVE_HIERARCHIES](https://msdn.microsoft.com/library/mt719104)     |  Сведения об объектах PerspectiveHierarchy в каждом объекте PerspectiveTable.       |
|[TMSCHEMA_PERSPECTIVE_MEASURES](https://msdn.microsoft.com/library/mt719135)     |    Сведения об объектах PerspectiveMeasure в каждом объекте PerspectiveTable.     |
|[TMSCHEMA_PERSPECTIVE_TABLES](https://msdn.microsoft.com/library/mt719272)     |    Сведения об объектах таблице в перспективе.     |
|[TMSCHEMA_PERSPECTIVES](https://msdn.microsoft.com/library/mt704340)     |     Сведения об объектах перспективы в модели.    |
|[TMSCHEMA_RELATIONSHIPS](https://msdn.microsoft.com/library/mt704355)     |    Сведения об объектах отношений в модели.     |
|[TMSCHEMA_ROLE_MEMBERSHIPS](https://msdn.microsoft.com/library/mt704584)     |  Сведения об объектах RoleMembership в каждой роли.      |
|[TMSCHEMA_ROLES](https://msdn.microsoft.com/library/mt719267)    |   Сведения об объектах роли в модели.      |
|[TMSCHEMA_TABLE_PERMISSIONS](https://msdn.microsoft.com/library/mt704347)    |    Сведения об объектах TablePermission в каждой роли.     |
|[TMSCHEMA_TABLES](https://msdn.microsoft.com/library/mt719250)     |   Сведения об объектах таблицы в модели.      |
|[TMSCHEMA_VARIATIONS](https://msdn.microsoft.com/library/mt825008)|Сведения об объектах вариантов в каждом столбце.|

### <a name="rowsets-described-in-the-ms-ssas-sql-server-analysis-services-protocol"></a>Наборы строк, описано в [MS-SSAS]: протокол служб анализа SQL Server

|Набор строк|Описание|  
|------------|-----------------|  
|[DBSCHEMA_CATALOGS](https://msdn.microsoft.com/library/ee302115)|Описывает каталоги, которые доступны на сервере.|  
|[DBSCHEMA_COLUMNS](https://msdn.microsoft.com/library/ee301789)|Возвращает строку для каждой меры, каждый атрибут измерения куба и каждый столбец набора строк схемы, в виде столбца.|  
|[DBSCHEMA_PROVIDER_TYPES](https://msdn.microsoft.com/library/ee301696)|Типы данных (базовый), поддерживаемые сервером.|  
|[DBSCHEMA_TABLES](https://msdn.microsoft.com/library/ee320843)|Возвращает измерения, группы мер или наборы строк схемы, представленные в виде таблиц.|  
|[DISCOVER_CALC_DEPENDENCY](https://msdn.microsoft.com/library/hh770226)| Возвращает сведения о зависимости вычисления для объекта, который указан в табличной базы данных или в запросе DAX, выполненного для табличной базы данных. |  
|[DISCOVER_COMMAND_OBJECTS](https://msdn.microsoft.com/library/ee320662)|Предоставляет сведения по использованию ресурсов и активности для объектов, которые используются указанной командой.|  
|[DISCOVER_COMMANDS](https://msdn.microsoft.com/library/ee320715)|Предоставляет сведения об использовании ресурсов и действиях, касающиеся выполняемых в настоящее время или последних выполненных команд в соединениях, открытых на сервере.|  
|[DISCOVER_CONNECTIONS](https://msdn.microsoft.com/library/ee301889)|Предоставляет сведения об использовании ресурсов и действиях, касающиеся соединений, открытых в настоящее время на сервере.|  
|[DISCOVER_CSDL_METADATA](https://msdn.microsoft.com/library/gg587670)|Возвращает сведения о метаданных базы данных для баз данных в памяти.|  
|[DISCOVER_DATASOURCES](https://msdn.microsoft.com/library/ee320285)|Возвращает список источников данных, доступных на сервере.|
|[DISCOVER_DB_CONNECTIONS](https://msdn.microsoft.com/library/ee320467)|Предоставляет сведения об использовании и действиях по открытым в настоящий момент соединениям сервера с базой данных.|  
|[DISCOVER_DIMENSION_STAT](https://msdn.microsoft.com/library/ee320284)|Возвращает статистику по указанному измерению.|  
|[DISCOVER_ENUMERATORS](https://msdn.microsoft.com/library/ee302012)|Возвращает список имен, типов данных и значений перечисления, поддерживаемых поставщиком XMLA для конкретного источника данных.|  
|[DISCOVER_INSTANCES](https://msdn.microsoft.com/library/ee320541)|Описывает экземпляры на сервере.|  
|[DISCOVER_JOBS](https://msdn.microsoft.com/library/ee320363)|Предоставляет сведения о текущих заданиях, выполняющихся на сервере. Задание представляет собой часть команды, которая осуществляет конкретную задачу в целях выполнения команды.|  
|[DISCOVER_KEYWORDS &AMP;#40;XML ДЛЯ АНАЛИТИКИ&AMP;#41;](https://msdn.microsoft.com/library/ee301719)|Возвращает сведения о ключевых словах, зарезервированных сервером XML для Аналитики.|  
|[DISCOVER_LITERALS](https://msdn.microsoft.com/library/ee301320)|Возвращает сведения о литералах, поддерживаемых сервером.|  
|[DISCOVER_LOCATIONS](https://msdn.microsoft.com/library/ee302024)|Возвращает сведения о содержимом файла резервной копии. |
|[DISCOVER_LOCKS](https://msdn.microsoft.com/library/ee320398)|Предоставляет сведения о текущих установленных блокировках на сервере.|  
|[DISCOVER_MASTER_KEY](https://msdn.microsoft.com/library/ee301825)|Возвращает ключ шифрования сервера.|
|[DISCOVER_MEMORYGRANT](https://msdn.microsoft.com/library/ee320945)|Возвращает список предоставленных квот внутренней памяти, занятых заданиями, которые сейчас выполняются на сервере.|  
|[DISCOVER_MEMORYUSAGE](https://msdn.microsoft.com/library/ee320910)|Возвращает статистику DISCOVER_MEMORYUSAGE для различных объектов, выделенных сервером.|  
|[DISCOVER_OBJECT_ACTIVITY](https://msdn.microsoft.com/library/ee320661)|Предоставляет сведения об использовании ресурсов каждым объектом с начала работы службы.|  
|[DISCOVER_OBJECT_MEMORY_USAGE](https://msdn.microsoft.com/library/ee320910)|Возвращает статистику DISCOVER_MEMORYUSAGE для различных объектов, выделенных сервером.|  
|[DISCOVER_PARTITION_DIMENSION_STAT](https://msdn.microsoft.com/library/ee320268)|Возвращает статистику по измерению, связанному с секцией.|  
|[DISCOVER_PARTITION_STAT](https://msdn.microsoft.com/library/ee320483)|Возвращает статистику по агрегатам в заданной секции.|  
|[DISCOVER_PERFORMANCE_COUNTERS](https://msdn.microsoft.com/library/ee320809)|Возвращает значение одного или нескольких указанных счетчиков производительности. |  
|[DISCOVER_PROPERTIES](https://msdn.microsoft.com/library/ee320589)|Возвращает список значения и сведения о свойствах, которые поддерживаются сервером для указанного источника данных.|  
|[DISCOVER_RING_BUFFERS](https://msdn.microsoft.com/library/mt719204)|Возвращает сведения о текущем кольцевые буферы XEvent на сервере.|
|[DISCOVER_SCHEMA_ROWSETS](https://msdn.microsoft.com/library/ee320478)|Возвращает имена, ограничения, описание и другие сведения для всех запросов распознавания.|  
|[DISCOVER_SESSIONS](https://msdn.microsoft.com/library/ee301962)|Предоставляет сведения об использовании и действиях для сеансов, открытых на сервере в данный момент.|  
|[DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS](https://msdn.microsoft.com/library/ee320710)|Возвращает сведения о столбце сегментов, используемых для хранения данных для таблиц в памяти.|  
|[DISCOVER_STORAGE_TABLE_COLUMNS](https://msdn.microsoft.com/library/ee302101)|Содержит сведения о столбцах, используемый для представления столбцов таблицы в памяти.|  
|[DISCOVER_STORAGE_TABLES](https://msdn.microsoft.com/library/ee302014)|Возвращает статистические данные о доступных таблиц в памяти на сервер.|  
|[DISCOVER_TRACE_COLUMNS]()||  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO](https://msdn.microsoft.com/library/ee301342)|Содержит набор строк схемы DISCOVER_TRACE_COLUMNS.|  
|[DISCOVER_TRACE_EVENT_CATEGORIES](https://msdn.microsoft.com/library/ee320442)|Содержит набор строк схемы DISCOVER_TRACE_EVENT_CATEGORIES.|  
|[DISCOVER_TRACES](https://msdn.microsoft.com/library/ee301643)|Содержит набор строк схемы DISCOVER_TRACES.|  
|[DISCOVER_TRANSACTIONS](https://msdn.microsoft.com/library/ee301363)|Возвращает текущий набор ожидающих транзакций в системе.|  
|[DISCOVER_XEVENT_TRACE_DEFINITION](https://msdn.microsoft.com/library/mt704568)|Содержит сведения о трассировках XEvent, которые в настоящее время активны на сервере.|  
|[DISCOVER_XEVENT_PACKAGES](https://msdn.microsoft.com/library/mt704569)|Предоставляет сведения о пакетах XEvent, которые описаны на сервере.|
|[DISCOVER_XEVENT_OBJECTS](https://msdn.microsoft.com/library/mt704543)|Предоставляет сведения об объектах XEvent, которые описаны на сервере.|
|[DISCOVER_XEVENT_OBJECT_COLUMNS](https://msdn.microsoft.com/library/mt719352)|Предоставляет сведения о схеме объектов XEvent, которые описаны на сервере.|
|[DISCOVER_XEVENT_SESSIONS](https://msdn.microsoft.com/library/mt704397)|Предоставляет сведения о текущих сеансов XEvent на сервере.|
|[DISCOVER_XEVENT_SESSION_TARGETS](https://msdn.microsoft.com/library/mt704564)|Предоставляет сведения о текущей цели сеанса XEvent на сервере.|
|[DISCOVER_XML_METADATA](https://msdn.microsoft.com/library/ee301560)|Возвращает набор строк с одной строкой и одним столбцом. |
|[DMSCHEMA_MINING_COLUMNS](https://msdn.microsoft.com/library/ee301664)|Описывает отдельные столбцы всех моделей интеллектуального анализа данных Описываемые данные, которые развертываются на сервере.|  
|[DMSCHEMA_MINING_FUNCTIONS](https://msdn.microsoft.com/library/ee320415)|Описывает функции интеллектуального анализа данных, поддерживаемых алгоритмов интеллектуального анализа данных, доступных на сервере под управлением служб Analysis Services.|  
|[DMSCHEMA_MINING_MODEL_CONTENT](https://msdn.microsoft.com/library/ee302124)|Позволяет клиентскому приложению просматривать содержимое модели интеллектуального анализа данных данные обучения.|  
|[DMSCHEMA_MINING_MODEL_CONTENT_PMML](https://msdn.microsoft.com/library/ee320692)|Возвращает XML-структуру модели интеллектуального анализа данных. Формат XML-строки соответствует стандарту PMML 2.1.|  
|[DMSCHEMA_MINING_MODEL_XML](https://msdn.microsoft.com/library/ee301916)|Возвращает XML-структуру модели интеллектуального анализа данных. Формат XML-строки соответствует стандарту PMML 2.1.|  
|[DMSCHEMA_MINING_MODELS](https://msdn.microsoft.com/library/ee320603)|Перечисляет модели интеллектуального анализа данных, которые развернуты на сервере.|  
|[DMSCHEMA_MINING_SERVICE_PARAMETERS](https://msdn.microsoft.com/library/ee320378)|Предоставляет список параметров, которые могут использоваться для настройки поведения каждого алгоритма интеллектуального анализа данных, установленного на сервере.|  
|[DMSCHEMA_MINING_SERVICES](https://msdn.microsoft.com/library/ee320487)|Сведения о каждом алгоритм интеллектуального анализа данных, которую поддерживает сервер.|  
|[DMSCHEMA_MINING_STRUCTURE_COLUMNS](https://msdn.microsoft.com/library/ee320277)|Описывает отдельные столбцы всех структур интеллектуального анализа данных, которые развернуты на сервере.|  
|[DMSCHEMA_MINING_STRUCTURES](https://msdn.microsoft.com/library/ee320704)|Перечисляет информацию о структурах интеллектуального анализа данных в текущем каталоге.|  
|[MDSCHEMA_ACTIONS](https://msdn.microsoft.com/library/ee320890)|Описывает действия, которые могут быть доступны клиентскому приложению.|
|[MDSCHEMA_CUBES](https://msdn.microsoft.com/library/ee301304)|Описывает структуру кубов в базе данных. Перспективы возвращаются в этой схеме.|
|[MDSCHEMA_DIMENSIONS](https://msdn.microsoft.com/library/ee301366)|Содержит описание измерений в базе данных.|  
|[MDSCHEMA_FUNCTIONS](https://msdn.microsoft.com/library/mt719467)|Возвращает сведения о функциях, доступных для использования в языках DAX и MDX.|
|[MDSCHEMA_HIERARCHIES](https://msdn.microsoft.com/library/ee320250)|Описывает каждую иерархию в конкретном измерении.|  
|[MDSCHEMA_INPUT_DATASOURCES](https://msdn.microsoft.com/library/ee301386)|Описывает объекты источника данных, описанной в базе данных.|  
|[MDSCHEMA_KPIS](https://msdn.microsoft.com/library/ee320406)|Описывает ключевые показатели эффективности в базе данных.|  
|[MDSCHEMA_LEVELS](https://msdn.microsoft.com/library/ee320746)|Описывает каждый уровень в конкретной иерархии.|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS](https://msdn.microsoft.com/library/ee320977)|Перечисляет измерения группы мер.|  
|[MDSCHEMA_MEASUREGROUPS](https://msdn.microsoft.com/library/ee320601)|Описывает группы мер в базе данных.|  
|[MDSCHEMA_MEASURES](https://msdn.microsoft.com/library/ee301871)|Описывает каждую меру.|  
|[MDSCHEMA_MEMBERS](https://msdn.microsoft.com/library/ee320960)|Описывает элементы в базе данных.|  
|[MDSCHEMA_PROPERTIES](https://msdn.microsoft.com/library/ee320393)|Описывает свойства элементов и ячеек.|  
|[MDSCHEMA_SETS](https://msdn.microsoft.com/library/ee301356)|Описывает любые наборы, которые описаны в данный момент в базе данных, включая наборы с областью сеанса.|  

> [!NOTE]
> Динамические административные представления ХРАНИЛИЩА нет набора строк схемы, описанные в протоколе.