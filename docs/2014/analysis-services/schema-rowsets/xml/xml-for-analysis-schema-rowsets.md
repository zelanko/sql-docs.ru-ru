---
title: XML для анализа наборов строк схемы | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- rowsets [Analysis Services], XML for Analysis
- XML for Analysis, schema rowsets
- schema rowsets [Analysis Services], XML for Analysis
- schema rowsets [XML for Analysis]
ms.assetid: 36e3ecfd-fcc3-415a-9c43-f59921d2468a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 50f95f4049d03c8d822c3e56ba5ff235705bf4de
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121184"
---
# <a name="xml-for-analysis-schema-rowsets"></a>XML for Analysis Schema Rowsets
  Поставщик [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) содержит наборы строк схемы, которые возвращают метаданные о состоянии, активности и объектах сервера. Получение метаданных необходимо, когда идет разработка клиентского приложения, подключающегося к модели служб Analysis Services, обладающей переменной структурой и характеристиками.  
  
 Наборы строк схемы также дают представление о внутренних процессах и операциях, что помогает в наблюдении за сервером и устранении неполадок. Для поддержки нерегламентированных административных задач можно выполнить запрос динамического административного представления к большинству наборов строк схемы. Запросы динамического административного представления возвращают результаты в удобном для чтения табличном формате. Их можно просматривать в среде [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].  
  
 В следующей таблице перечислены все наборы строк схемы XMLA, даны их описания и указано, какие запросы возвращают сведения, относящиеся к табличным моделям данных.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Набор строк<sup>1</sup>|Описание|  
|------------------------|-----------------|  
|[Набор строк DISCOVER_CALC_DEPENDENCY](discover-calc-dependency-rowset.md)|Возвращает сведения о зависимостях между таблицами, столбцами, мерами и формулами для вычисляемых столбцов.<br /><br /> Применяется к табличным моделям, развернутым в экземпляре служб Analysis Services, и моделям PowerPivot в книгах Excel, которые работают в среде SharePoint.|  
|[Набор строк DISCOVER_CONNECTIONS](discover-connections-rowset.md)|Предоставляет сведения об использовании ресурсов и действиях, касающиеся соединений, открытых в настоящее время на сервере.|  
|[Набор строк DISCOVER_COMMAND_OBJECTS](discover-command-objects-rowset.md)|Предоставляет сведения по использованию ресурсов и активности для объектов, которые используются указанной командой.|  
|[Набор строк DISCOVER_COMMANDS](discover-commands-rowset.md)|Предоставляет сведения об использовании ресурсов и действиях, касающихся выполняемых в настоящее время или последних выполненных команд в соединениях, открытых на сервере.|  
|[Набор строк DISCOVER_CSDL_METADATA](discover-csdl-metadata-rowset.md)|Возвращает XML-определение источника данных клиенту, который может обрабатывать табличную модель или модель PowerPivot и представить источник данных как часть отчета.<br /><br /> Применяется к табличным моделям, развернутым в экземпляре служб Analysis Services, и моделям PowerPivot в книгах Excel, которые работают в среде SharePoint.|  
|[Набор строк DISCOVER_DATASOURCES](discover-datasources-rowset.md)|Возвращает список источников данных поставщика XMLA, которые доступны на сервере или в веб-службе.|  
|[Набор строк DISCOVER_DB_CONNECTIONS](discover-db-connections-rowset.md)|Предоставляет сведения об использовании и действиях по открытым в настоящий момент соединениям сервера с базой данных.|  
|[Набор строк DISCOVER_DIMENSION_STAT](discover-dimension-stat-rowset.md)|Возвращает статистику по указанному измерению.|  
|[Набор строк DISCOVER_ENUMERATORS](discover-enumerators-rowset.md)|Возвращает список имен, типов данных и значений перечисления, поддерживаемых поставщиком XMLA для конкретного источника данных.|  
|[Набор строк DISCOVER_JOBS](discover-jobs-rowset.md)|Предоставляет сведения о текущих заданиях, выполняющихся на сервере.|  
|[Набор строк DISCOVER_KEYWORDS &#40;XML для Аналитики&#41;](discover-keywords-rowset-xmla.md)|Возвращает сведения о ключевых словах, зарезервированных поставщиком XMLA.|  
|[Набор строк DISCOVER_LITERALS](discover-literals-rowset.md)|Возвращает сведения о литералах, включая типы данных и значения, поддерживаемые поставщиком XMLA.|  
|[Набор строк DISCOVER_LOCATIONS](discover-locations-rowset.md)|Возвращает сведения о содержимом файла резервной копии.|  
|[Набор строк DISCOVER_LOCKS](discover-locks-rowset.md)|Предоставляет сведения о текущих установленных блокировках на сервере.|  
|[Набор строк DISCOVER_MEMORYGRANT](discover-memorygrant-rowset.md)|Возвращает список предоставленных квот внутренней памяти, занятых заданиями, которые сейчас выполняются на сервере.|  
|[Набор строк DISCOVER_MEMORYUSAGE](discover-memoryusage-rowset.md)|Возвращает статистику использования памяти для различных объектов, выделенных сервером.|  
|[Набор строк DISCOVER_OBJECT_ACTIVITY](discover-object-activity-rowset.md)|Предоставляет сведения об использовании ресурсов каждым объектом с начала работы службы.|  
|[Набор строк DISCOVER_OBJECT_MEMORY_USAGE](discover-object-memory-usage-rowset.md)|Предоставляет сведения об использовании ресурсов памяти объектами.|  
|[Набор строк DISCOVER_PARTITION_DIMENSION_STAT](discover-partition-dimension-stat-rowset.md)|Возвращает статистику по измерению, связанному с секцией.|  
|[Набор строк DISCOVER_PARTITION_STAT](discover-partition-stat-rowset.md)|Возвращает статистику по агрегатам в заданной секции.|  
|[Набор строк DISCOVER_PERFORMANCE_COUNTERS](discover-performance-counters-rowset.md)|Возвращает значение одного или нескольких указанных счетчиков производительности.|  
|[Набор строк DISCOVER_PROPERTIES](discover-properties-rowset.md)|Возвращает список сведений и значений для стандартных свойств и свойств, зависящих от конкретного поставщика, поддерживаемых поставщиком XMLA для указанного источника данных.|  
|[Набор строк DISCOVER_SCHEMA_ROWSETS](discover-schema-rowsets-rowset.md)|Возвращает имена, ограничения, описание и другие сведения для всех значений перечисления и для дополнительных значений перечисления, зависящих от конкретного поставщика, поддерживаемых поставщиком XMLA.|  
|[Набор строк DISCOVER_SESSIONS](discover-sessions-rowset.md)|Предоставляет сведения об использовании и действиях для сеансов, открытых на сервере в данный момент.|  
|[Набор строк DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS](discover-storage-table-column-segments-rowset.md)|Содержит сведения на уровне столбцов и сегментов о таблицах хранения, используемых табличной базой данных или базой данных PowerPivot.<br /><br /> Применяется к табличным моделям, развернутым в экземпляре служб Analysis Services, и моделям PowerPivot в книгах Excel, которые работают в среде SharePoint.|  
|[Набор строк DISCOVER_STORAGE_TABLE_COLUMNS](discover-storage-table-columns-rowset.md)|Позволяет клиенту определить назначение столбцов для таблиц хранения, используемых в табличной базе данных или базе данных PowerPivot.<br /><br /> Применяется к табличным моделям, развернутым в экземпляре служб Analysis Services, и моделям PowerPivot в книгах Excel, которые работают в среде SharePoint.|  
|[Набор строк DISCOVER_STORAGE_TABLES](discover-storage-tables-rowset.md)|Возвращает сведения о таблицах, используемых в модели.<br /><br /> Применяется к табличным моделям, развернутым в экземпляре служб Analysis Services, и моделям PowerPivot в книгах Excel, которые работают в среде SharePoint.|  
|[Набор строк DISCOVER_TRACE_COLUMNS](discover-trace-columns-rowset.md)|Описывает столбцы трассировки, предоставляемые поставщиком трассировки.|  
|[Набор строк DISCOVER_TRACE_DEFINITION_PROVIDERINFO](discover-trace-definition-providerinfo-rowset.md)|Возвращает основные сведения о поставщике трассировки, в том числе его имя и описание.|  
|[Набор строк DISCOVER_TRACE_EVENT_CATEGORIES](discover-trace-event-categories-rowset.md)|Описывает категории событий, предоставляемые поставщиком трассировки.|  
|[Набор строк DISCOVER_TRACES](discover-traces-rowset.md)|Возвращает сведения о трассировках, запущенных на сервере.|  
|[Набор строк DISCOVER_TRANSACTIONS](discover-transactions-rowset.md)|Возвращает текущий набор ожидающих транзакций в системе.|  
|[Набор строк DISCOVER_XML_METADATA](discover-xml-metadata-rowset.md)|Возвращает XML-документ с описанием запрошенного объекта.|  
  
 <sup>1</sup> все наборы строк схемы, перечисленные здесь поддерживаются поставщиком источника данных MSOLAP для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] поставщика XML для Аналитики.  
  
## <a name="see-also"></a>См. также  
 [Разработка с использованием XMLA в службах Analysis Services](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)   
 [Используйте динамические административные представления &#40;динамические административные представления&#41; мониторинг Analysis Services](../../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)   
 [Получение метаданных из источника аналитических данных](../../multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  
