---
title: "Наборы строк схемы анализа XML для | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- rowsets [Analysis Services], XML for Analysis
- XML for Analysis, schema rowsets
- schema rowsets [Analysis Services], XML for Analysis
- schema rowsets [XML for Analysis]
ms.assetid: 36e3ecfd-fcc3-415a-9c43-f59921d2468a
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 44c9f6740001c80fd01eaaf53f735bc539f39036
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="xml-for-analysis-schema-rowsets"></a>XML for Analysis Schema Rowsets
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщик содержит наборы строк схемы, которые возвращают метаданные о состоянии сервера, действия и объекты. Получение метаданных необходимо, когда идет разработка клиентского приложения, подключающегося к модели служб Analysis Services, обладающей переменной структурой и характеристиками.  
  
 Наборы строк схемы также дают представление о внутренних процессах и операциях, что помогает в наблюдении за сервером и устранении неполадок. Для поддержки нерегламентированных административных задач можно выполнить запрос динамического административного представления к большинству наборов строк схемы. Запросы динамического административного представления возвращают результаты в удобном для чтения табличном формате. Их можно просматривать в среде [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].  
  
 В следующей таблице перечислены все наборы строк схемы XMLA, даны их описания и указано, какие запросы возвращают сведения, относящиеся к табличным моделям данных.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Набор строк<sup>1</sup>|Description|  
|------------------------|-----------------|  
|[Набор строк DISCOVER_CALC_DEPENDENCY](../../../analysis-services/schema-rowsets/xml/discover-calc-dependency-rowset.md)|Возвращает сведения о зависимостях между таблицами, столбцами, мерами и формулами для вычисляемых столбцов.<br /><br /> Применяется к табличным моделям, развернутая на экземпляре служб Analysis Services и [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] моделей в книгах Excel, которые выполняются в среде SharePoint.|  
|[Набор строк DISCOVER_CONNECTIONS](../../../analysis-services/schema-rowsets/xml/discover-connections-rowset.md)|Предоставляет сведения об использовании ресурсов и действиях, касающиеся соединений, открытых в настоящее время на сервере.|  
|[Набор строк DISCOVER_COMMAND_OBJECTS](../../../analysis-services/schema-rowsets/xml/discover-command-objects-rowset.md)|Предоставляет сведения по использованию ресурсов и активности для объектов, которые используются указанной командой.|  
|[Набор строк DISCOVER_COMMANDS](../../../analysis-services/schema-rowsets/xml/discover-commands-rowset.md)|Предоставляет сведения об использовании ресурсов и действиях, касающихся выполняемых в настоящее время или последних выполненных команд в соединениях, открытых на сервере.|  
|[Набор строк DISCOVER_CSDL_METADATA](../../../analysis-services/schema-rowsets/xml/discover-csdl-metadata-rowset.md)|Возвращает XML-определение источника данных клиенту, который может обрабатывать табличную или [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] модели и представить источник данных как часть отчета.<br /><br /> Применяется к табличным моделям, развернутая на экземпляре служб Analysis Services и [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] моделей в книгах Excel, которые выполняются в среде SharePoint.|  
|[Набор строк DISCOVER_DATASOURCES](../../../analysis-services/schema-rowsets/xml/discover-datasources-rowset.md)|Возвращает список источников данных поставщика XMLA, которые доступны на сервере или в веб-службе.|  
|[Набор строк DISCOVER_DB_CONNECTIONS](../../../analysis-services/schema-rowsets/xml/discover-db-connections-rowset.md)|Предоставляет сведения об использовании и действиях по открытым в настоящий момент соединениям сервера с базой данных.|  
|[Набор строк DISCOVER_DIMENSION_STAT](../../../analysis-services/schema-rowsets/xml/discover-dimension-stat-rowset.md)|Возвращает статистику по указанному измерению.|  
|[Набор строк DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)|Возвращает список имен, типов данных и значений перечисления, поддерживаемых поставщиком XMLA для конкретного источника данных.|  
|[Набор строк DISCOVER_JOBS](../../../analysis-services/schema-rowsets/xml/discover-jobs-rowset.md)|Предоставляет сведения о текущих заданиях, выполняющихся на сервере.|  
|[Набор строк DISCOVER_KEYWORDS &#40; XML для Аналитики &#41;](../../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)|Возвращает сведения о ключевых словах, зарезервированных поставщиком XMLA.|  
|[Набор строк DISCOVER_LITERALS](../../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)|Возвращает сведения о литералах, включая типы данных и значения, поддерживаемые поставщиком XMLA.|  
|[Набор строк DISCOVER_LOCATIONS](../../../analysis-services/schema-rowsets/xml/discover-locations-rowset.md)|Возвращает сведения о содержимом файла резервной копии.|  
|[Набор строк DISCOVER_LOCKS](../../../analysis-services/schema-rowsets/xml/discover-locks-rowset.md)|Предоставляет сведения о текущих установленных блокировках на сервере.|  
|[Набор строк DISCOVER_MEMORYGRANT](../../../analysis-services/schema-rowsets/xml/discover-memorygrant-rowset.md)|Возвращает список предоставленных квот внутренней памяти, занятых заданиями, которые сейчас выполняются на сервере.|  
|[Набор строк DISCOVER_MEMORYUSAGE](../../../analysis-services/schema-rowsets/xml/discover-memoryusage-rowset.md)|Возвращает статистику использования памяти для различных объектов, выделенных сервером.|  
|[Набор строк DISCOVER_OBJECT_ACTIVITY](../../../analysis-services/schema-rowsets/xml/discover-object-activity-rowset.md)|Предоставляет сведения об использовании ресурсов каждым объектом с начала работы службы.|  
|[Набор строк DISCOVER_OBJECT_MEMORY_USAGE](../../../analysis-services/schema-rowsets/xml/discover-object-memory-usage-rowset.md)|Предоставляет сведения об использовании ресурсов памяти объектами.|  
|[Набор строк DISCOVER_PARTITION_DIMENSION_STAT](../../../analysis-services/schema-rowsets/xml/discover-partition-dimension-stat-rowset.md)|Возвращает статистику по измерению, связанному с секцией.|  
|[Набор строк DISCOVER_PARTITION_STAT](../../../analysis-services/schema-rowsets/xml/discover-partition-stat-rowset.md)|Возвращает статистику по агрегатам в заданной секции.|  
|[Набор строк DISCOVER_PERFORMANCE_COUNTERS](../../../analysis-services/schema-rowsets/xml/discover-performance-counters-rowset.md)|Возвращает значение одного или нескольких указанных счетчиков производительности.|  
|[Набор строк DISCOVER_PROPERTIES](../../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md)|Возвращает список сведений и значений для стандартных свойств и свойств, зависящих от конкретного поставщика, поддерживаемых поставщиком XMLA для указанного источника данных.|  
|[Набор строк DISCOVER_SCHEMA_ROWSETS](../../../analysis-services/schema-rowsets/xml/discover-schema-rowsets-rowset.md)|Возвращает имена, ограничения, описание и другие сведения для всех значений перечисления и для дополнительных значений перечисления, зависящих от конкретного поставщика, поддерживаемых поставщиком XMLA.|  
|[Набор строк DISCOVER_SESSIONS](../../../analysis-services/schema-rowsets/xml/discover-sessions-rowset.md)|Предоставляет сведения об использовании и действиях для сеансов, открытых на сервере в данный момент.|  
|[Набор строк DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS](../../../analysis-services/schema-rowsets/xml/discover-storage-table-column-segments-rowset.md)|Предоставляет сведения на уровне столбцов и сегментов о таблицах хранилища, используемых в табличную или [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] базы данных.<br /><br /> Применяется к табличным моделям, развернутая на экземпляре служб Analysis Services и [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] моделей в книгах Excel, которые выполняются в среде SharePoint.|  
|[Набор строк DISCOVER_STORAGE_TABLE_COLUMNS](../../../analysis-services/schema-rowsets/xml/discover-storage-table-columns-rowset.md)|Позволяет клиенту определить назначение столбцов таблиц хранилища, используемые табличную или [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] базы данных.<br /><br /> Применяется к табличным моделям, развернутая на экземпляре служб Analysis Services и [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] моделей в книгах Excel, которые выполняются в среде SharePoint.|  
|[Набор строк DISCOVER_STORAGE_TABLES](../../../analysis-services/schema-rowsets/xml/discover-storage-tables-rowset.md)|Возвращает сведения о таблицах, используемых в модели.<br /><br /> Применяется к табличным моделям, развернутая на экземпляре служб Analysis Services и [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] моделей в книгах Excel, которые выполняются в среде SharePoint.|  
|[Набор строк DISCOVER_TRACE_COLUMNS](../../../analysis-services/schema-rowsets/xml/discover-trace-columns-rowset.md)|Описывает столбцы трассировки, предоставляемые поставщиком трассировки.|  
|[Набор строк DISCOVER_TRACE_DEFINITION_PROVIDERINFO](../../../analysis-services/schema-rowsets/xml/discover-trace-definition-providerinfo-rowset.md)|Возвращает основные сведения о поставщике трассировки, в том числе его имя и описание.|  
|[Набор строк DISCOVER_TRACE_EVENT_CATEGORIES](../../../analysis-services/schema-rowsets/xml/discover-trace-event-categories-rowset.md)|Описывает категории событий, предоставляемые поставщиком трассировки.|  
|[Набор строк DISCOVER_TRACES](../../../analysis-services/schema-rowsets/xml/discover-traces-rowset.md)|Возвращает сведения о трассировках, запущенных на сервере.|  
|[Набор строк DISCOVER_TRANSACTIONS](../../../analysis-services/schema-rowsets/xml/discover-transactions-rowset.md)|Возвращает текущий набор ожидающих транзакций в системе.|  
|[Набор строк DISCOVER_XML_METADATA](../../../analysis-services/schema-rowsets/xml/discover-xml-metadata-rowset.md)|Возвращает XML-документ с описанием запрошенного объекта.|  
  
 <sup>1</sup> все наборы строк схемы, приведенные здесь поддерживаются поставщиком источника данных MSOLAP для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] поставщика XML для Аналитики.  
  
## <a name="see-also"></a>См. также:  
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)   
 [Используйте динамические административные представления &#40; динамических административных представлений &#41; для мониторинга служб Analysis Services](../../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)   
 [Получение метаданных из источника аналитических данных](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  
