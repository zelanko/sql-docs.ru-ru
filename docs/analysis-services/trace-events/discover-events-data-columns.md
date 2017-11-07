---
title: "Столбцы данных событий обнаружения | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Discover Events event category
ms.assetid: 10ec598e-5b51-4767-b4f7-42e261d96a40
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1d4275dc8ed85c907a458c5772a57153dc88fa0e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="discover-events-data-columns"></a>Столбцы данных событий обнаружения
  Категория событий «События обнаружения» содержит следующие классы событий:  
  
-   Класс "Начало обнаружения"  
  
-   Класс "Завершение обнаружения"  
  
 В следующих таблицах перечисляются столбцы данных для каждого из этих классов событий.  
  
## <a name="discover-begin-classdata-columns"></a>Класс «Начало обнаружения» — столбцы данных  
  
|||||  
|-|-|-|-|  
|**Имя столбца**|**Идентификатор столбца**|**Тип столбца**|**Описание столбца**|  
|EventClass|0|1|Класс событий используется для категоризации событий.|  
|EventSubclass|1|1|Подкласс событий предоставляет дополнительные сведения о каждом классе событий.  Допустимы следующие пары значений **Идентификатор подкласса**/**Имя подкласса** :<br /><br /> 0: DBSCHEMA_CATALOGS<br /><br /> 1: DBSCHEMA_TABLES<br /><br /> 2: DBSCHEMA_COLUMNS<br /><br /> 3: DBSCHEMA_PROVIDER_TYPES<br /><br /> 4: MDSCHEMA_CUBES<br /><br /> 5: MDSCHEMA_DIMENSIONS<br /><br /> 6: MDSCHEMA_HIERARCHIES<br /><br /> 7: MDSCHEMA_LEVELS<br /><br /> 8: MDSCHEMA_MEASURES<br /><br /> 9: MDSCHEMA_PROPERTIES<br /><br /> 10: MDSCHEMA_MEMBERS<br /><br /> 11: MDSCHEMA_FUNCTIONS<br /><br /> 12: MDSCHEMA_ACTIONS<br /><br /> 13: MDSCHEMA_SETS<br /><br /> 14: DISCOVER_INSTANCES<br /><br /> 15: MDSCHEMA_KPIS<br /><br /> 16: MDSCHEMA_MEASUREGROUPS<br /><br /> 17: MDSCHEMA_COMMANDS<br /><br /> 18: DMSCHEMA_MINING_SERVICES<br /><br /> 19: DMSCHEMA_MINING_SERVICE_PARAMETERS<br /><br /> 20: DMSCHEMA_MINING_FUNCTIONS<br /><br /> 21: DMSCHEMA_MINING_MODEL_CONTENT<br /><br /> 22: DMSCHEMA_MINING_MODEL_XML<br /><br /> 23: DMSCHEMA_MINING_MODELS<br /><br /> 24: DMSCHEMA_MINING_COLUMNS<br /><br /> 25: DISCOVER_DATASOURCES<br /><br /> 26: DISCOVER_PROPERTIES<br /><br /> 27: DISCOVER_SCHEMA_ROWSETS<br /><br /> 28: DISCOVER_ENUMERATORS<br /><br /> 29: DISCOVER_KEYWORDS<br /><br /> 30: DISCOVER_LITERALS<br /><br /> 31: DISCOVER_XML_METADATA<br /><br /> 32: DISCOVER_TRACES<br /><br /> 33: DISCOVER_TRACE_DEFINITION_PROVIDERINFO<br /><br /> 34: DISCOVER_TRACE_COLUMNS<br /><br /> 35: DISCOVER_TRACE_EVENT_CATEGORIES<br /><br /> 36: DMSCHEMA_MINING_STRUCTURES<br /><br /> 37: DMSCHEMA_MINING_STRUCTURE_COLUMNS<br /><br /> 38: DISCOVER_MASTER_KEY<br /><br /> 39: MDSCHEMA_INPUT_DATASOURCES<br /><br /> 40: DISCOVER_LOCATIONS<br /><br /> 41: DISCOVER_PARTITION_DIMENSION_STAT<br /><br /> 42: DISCOVER_PARTITION_STAT<br /><br /> 43: DISCOVER_DIMENSION_STAT<br /><br /> 44: MDSCHEMA_MEASUREGROUP_DIMENSIONS<br /><br /> 49: DISCOVER_XEVENT_TRACE_DEFINITION|  
|CurrentTime|2|5|Время начала события, если оно доступно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|StartTime|3|5|Время начала события, если оно доступно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|ConnectionID|25|1|Содержит уникальный идентификатор соединения, сопоставленный с событием обнаружения.|  
|DatabaseName|28|8|Имя базы данных, в которой выполняется инструкция пользователя.|  
|NTUserName|32|8|Содержит имя пользователя Windows, сопоставленное с событием обнаружения. Имя пользователя указано в канонической форме. Например, engineering.microsoft.com/software/user.|  
|NTDomainName|33|8|Содержит домен Windows, связанный с событием обнаружения.|  
|ClientProcessID|36|1|Содержит идентификатор процесса клиентского приложения.|  
|ApplicationName|37|8|Имя клиентского приложения, создавшего соединение с сервером. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|  
|SessionID|39|8|Содержит идентификатор сеанса, сопоставленный с событием обнаружения.|  
|NTCanonicalUserName|40|8|Содержит имя пользователя Windows, сопоставленное с событием обнаружения. Имя пользователя указано в канонической форме. Например, engineering.microsoft.com/software/user.|  
|SPID|41|1|Содержит идентификатор серверного процесса (SPID), который уникальным образом определяет пользовательский сеанс, связанный с событием обнаружения. Идентификатор SPID напрямую соответствует идентификатору GUID сеанса, используемому XML для аналитики.|  
|TextData|42|9|Содержит текстовые данные, связанные с событием.|  
|ServerName|43|8|Содержит имя экземпляра служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , в котором произошло событие обнаружения.|  
|RequestProperties|45|9|Содержит свойства запроса XML для аналитики (XMLA), связанного с событием обнаружения.|  
  
## <a name="discover-end-classdata-columns"></a>Класс «Конец обнаружения» — столбцы данных  
  
|||||  
|-|-|-|-|  
|**Имя столбца**|**Идентификатор столбца**|**Тип столбца**|**Описание столбца**|  
|EventClass|0|1|Содержит класс событий; он используется для категоризации событий.|  
|EventSubclass|1|1|Подкласс событий предоставляет дополнительные сведения о каждом классе событий. Допустимы следующие пары значений **Идентификатор подкласса**/**Имя подкласса** :<br /><br /> 0: DBSCHEMA_CATALOGS<br /><br /> 1: DBSCHEMA_TABLES<br /><br /> 2: DBSCHEMA_COLUMNS<br /><br /> 3: DBSCHEMA_PROVIDER_TYPES<br /><br /> 4: MDSCHEMA_CUBES<br /><br /> 5: MDSCHEMA_DIMENSIONS<br /><br /> 6: MDSCHEMA_HIERARCHIES<br /><br /> 7: MDSCHEMA_LEVELS<br /><br /> 8: MDSCHEMA_MEASURES<br /><br /> 9: MDSCHEMA_PROPERTIES<br /><br /> 10: MDSCHEMA_MEMBERS<br /><br /> 11: MDSCHEMA_FUNCTIONS<br /><br /> 12: MDSCHEMA_ACTIONS<br /><br /> 13: MDSCHEMA_SETS<br /><br /> 14: DISCOVER_INSTANCES<br /><br /> 15: MDSCHEMA_KPIS<br /><br /> 16: MDSCHEMA_MEASUREGROUPS<br /><br /> 17: MDSCHEMA_COMMANDS<br /><br /> 18: DMSCHEMA_MINING_SERVICES<br /><br /> 19: DMSCHEMA_MINING_SERVICE_PARAMETERS<br /><br /> 20: DMSCHEMA_MINING_FUNCTIONS<br /><br /> 21: DMSCHEMA_MINING_MODEL_CONTENT<br /><br /> 22: DMSCHEMA_MINING_MODEL_XML<br /><br /> 23: DMSCHEMA_MINING_MODELS<br /><br /> 24: DMSCHEMA_MINING_COLUMNS<br /><br /> 25: DISCOVER_DATASOURCES<br /><br /> 26: DISCOVER_PROPERTIES<br /><br /> 27: DISCOVER_SCHEMA_ROWSETS<br /><br /> 28: DISCOVER_ENUMERATORS<br /><br /> 29: DISCOVER_KEYWORDS<br /><br /> 30: DISCOVER_LITERALS<br /><br /> 31: DISCOVER_XML_METADATA<br /><br /> 32: DISCOVER_TRACES<br /><br /> 33: DISCOVER_TRACE_DEFINITION_PROVIDERINFO<br /><br /> 34: DISCOVER_TRACE_COLUMNS<br /><br /> 35: DISCOVER_TRACE_EVENT_CATEGORIES<br /><br /> 36: DMSCHEMA_MINING_STRUCTURES<br /><br /> 37: DMSCHEMA_MINING_STRUCTURE_COLUMNS<br /><br /> 38: DISCOVER_MASTER_KEY<br /><br /> 39: MDSCHEMA_INPUT_DATASOURCES<br /><br /> 40: DISCOVER_LOCATIONS<br /><br /> 41: DISCOVER_PARTITION_DIMENSION_STAT<br /><br /> 42: DISCOVER_PARTITION_STAT<br /><br /> 43: DISCOVER_DIMENSION_STAT<br /><br /> 44: MDSCHEMA_MEASUREGROUP_DIMENSIONS<br /><br /> 49: DISCOVER_XEVENT_TRACE_DEFINITION|  
|CurrentTime|2|5|Содержит текущее время события обнаружения, если доступно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|StartTime|3|5|Содержит время (если доступно) возникновения события окончания обнаружения. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|EndTime|4|5|Содержит время окончания события. Этот столбец не заполняется для таких классов событий запуска, как SQL:BatchStarting или SP:Starting. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|Длительность|5|2|Содержит приблизительное количество времени (в миллисекундах), которое заняло событие обнаружения.|  
|CPUTime|6|2|Содержит время ЦП в миллисекундах, использованного событием.|  
|Severity|22|1|Содержит степень серьезности исключения.|  
|Успешно|23|1|Содержит результат события обнаружения. Возможны следующие значения.<br /><br /> 0 = неуспешное завершение;<br /><br /> 1 = успешное завершение.|  
|Ошибка|24|1|Содержит номер любой ошибки, связанной с событием обнаружения.|  
|ConnectionID|25|1|Содержит уникальный идентификатор соединения, сопоставленный с событием обнаружения.|  
|DatabaseName|28|8|Содержит имя базы данных, в которой произошло событие обнаружения.|  
|NTUserName|32|8|Содержит имя пользователя Windows, сопоставленное с событием разрешения объекта.|  
|NTDomainName|33|8|Содержит учетную запись домена Windows, сопоставленную с событием обнаружения.|  
|ClientProcessID|36|1|Содержит идентификатор клиентского процесса для приложения, инициировавшего событие.|  
|ApplicationName|37|8|Содержит имя клиентского приложения, создавшего соединение с сервером. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|  
|SessionID|39|8|Содержит идентификатор сеанса, сопоставленный с событием обнаружения.|  
|NTCanonicalUserName|40|8|Содержит имя пользователя Windows, сопоставленное с событием разрешения объекта. Имя пользователя указано в канонической форме. Например, engineering.microsoft.com/software/user.|  
|SPID|41|1|Содержит идентификатор серверного процесса (SPID), который уникальным образом определяет пользовательский сеанс, связанный с событием окончания обнаружения. Идентификатор SPID напрямую соответствует идентификатору GUID сеанса, используемому XML для аналитики.|  
|TextData|42|9|Содержит текстовые данные, связанные с событием.|  
|ServerName|43|8|Содержит имя экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , в котором произошло событие обнаружения.|  
|RequestProperties|45|9|Содержит свойства в запросе XMLA.|  
  
## <a name="see-also"></a>См. также  
 [Discover Events Event Category](../../analysis-services/trace-events/discover-events-event-category.md)  
  
  

