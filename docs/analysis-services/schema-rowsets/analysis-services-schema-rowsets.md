---
title: Наборы строк схемы служб аналитики | Документация Майкрософт
ms.date: 10/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4ec9d6c75ef1d3cdc8effdc44861eed5971ced60
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116684"
---
# <a name="analysis-services-schema-rowsets"></a>Наборы строк схемы служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Наборы строк схемы — это стандартные таблицы, которые содержат сведения об объектах служб Analysis Services и состоянии сервера, включая схему базы данных, активные сеансы, соединения, а также выполняемые сервером команды и задания. Можно запрашивать таблицы набора строк схемы в окне скрипта XML для аналитики в среде SQL Server Management Studio, выполнять к набору строк схемы запрос динамического административного представления или создавать пользовательские приложения, содержащие сведения о наборе строк схемы (например, приложение для составления отчетов, которое получает список доступных измерений, используемый для создания отчета).  
  
> [!NOTE]  
>  При использовании наборов строк схемы в XML/A скрипт, данные, которые возвращаются в *результат* параметр [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) структурированы в соответствии с расположениями столбцов набора строк, описанный в этом раздел. [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщик поддерживает наборы строк, требуемые для анализа спецификации XML. Поставщик XMLA поддерживает также некоторые из наборов строк стандартной схемы для OLE DB, OLE DB для OLAP и OLE DB для поставщиков интеллектуального анализа данных. Поддерживаемые наборы строк описываются в следующих подразделах.  

Наборы строк схемы, описанные в двух протоколов SQL Server Analysis Services:   

[[MS-SSAS-T]: SQL Server Analysis Services табличному протоколу](https://msdn.microsoft.com/library/mt719260) -описывает наборы строк схемы для табличных моделей на уровне совместимости 1200 и выше.

[[MS-SSAS]: протокол служб SQL Server Analysis](https://msdn.microsoft.com/library/ee320606) -описывает наборы строк схемы для многомерных и табличных моделей на уровни совместимости 1100 и 1103.

## <a name="rowsets-described-in-the-ms-ssas-t-sql-server-analysis-services-tabular-protocol"></a>Наборы строк, описано в [MS-SSAS-T]: SQL Server Analysis Services табличному протоколу

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

## <a name="rowsets-described-in-the-ms-ssas-sql-server-analysis-services-protocol"></a>Наборы строк, описано в [MS-SSAS]: протокол служб анализа SQL Server

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

  
  
