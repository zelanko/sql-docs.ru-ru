---
title: Столбцы данных событий обнаружения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Discover Events event category
ms.assetid: 10ec598e-5b51-4767-b4f7-42e261d96a40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 72e462ead8fc003102bbd5ec1e48ef29904d0fb9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106244"
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
|EventSubclass|1|1|Подкласс событий предоставляет дополнительные сведения о каждом классе событий. Ниже приведены допустимые значения: имя пары:<br /><br /> 0: **DBSCHEMA_CATALOGS**<br />1: **DBSCHEMA_TABLES**<br />2: **DBSCHEMA_COLUMNS**<br />3: **DBSCHEMA_PROVIDER_TYPES**<br />4: **MDSCHEMA_CUBES**<br />5: **MDSCHEMA_DIMENSIONS**<br />6: **MDSCHEMA_HIERARCHIES**<br />7: **MDSCHEMA_LEVELS**<br />8: **MDSCHEMA_MEASURES**<br />9: **MDSCHEMA_PROPERTIES**<br />10: **MDSCHEMA_MEMBERS**<br />11: **MDSCHEMA_FUNCTIONS**<br />12: **MDSCHEMA_ACTIONS**<br />13: **MDSCHEMA_SETS**<br />14: **DISCOVER_INSTANCES**<br />15: **MDSCHEMA_KPIS**<br />16: **MDSCHEMA_MEASUREGROUPS**<br />17: **MDSCHEMA_COMMANDS**<br />18: **DMSCHEMA_MINING_SERVICES**<br />19: **DMSCHEMA_MINING_SERVICE_PARAMETERS**<br />20: **DMSCHEMA_MINING_FUNCTIONS**<br />21: **DMSCHEMA_MINING_MODEL_CONTENT**<br />22: **DMSCHEMA_MINING_MODEL_XML**<br />23: **DMSCHEMA_MINING_MODELS**<br />24: **DMSCHEMA_MINING_COLUMNS**<br />25: **DISCOVER_DATASOURCES**<br />26: **DISCOVER_PROPERTIES**<br />27: **DISCOVER_SCHEMA_ROWSETS**<br />28: **DISCOVER_ENUMERATORS**<br />29: **DISCOVER_KEYWORDS**<br />30: **DISCOVER_LITERALS**<br />31: **DISCOVER_XML_METADATA**<br />32: **DISCOVER_TRACES**<br />33: **DISCOVER_TRACE_DEFINITION_PROVIDERINFO**<br />34: **DISCOVER_TRACE_COLUMNS**<br />35: **DISCOVER_TRACE_EVENT_CATEGORIES**<br />36: **DMSCHEMA_MINING_STRUCTURES**<br />37: **DMSCHEMA_MINING_STRUCTURE_COLUMNS**<br />38: **DISCOVER_MASTER_KEY**<br />39: **MDSCHEMA_INPUT_DATASOURCES**<br />40: **DISCOVER_LOCATIONS**<br />41: **DISCOVER_PARTITION_DIMENSION_STAT**<br />42: **DISCOVER_PARTITION_STAT**<br />43: **DISCOVER_DIMENSION_STAT**<br />44: **MDSCHEMA_MEASUREGROUP_DIMENSIONS**<br />45: **DISCOVER_XEVENT_TRACE_DEFINITION**|  
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
|EventSubclass|1|1|Подкласс событий предоставляет дополнительные сведения о каждом классе событий. Ниже приведены допустимые значения: имя пары:<br /><br /> 0: **DBSCHEMA_CATALOGS**<br />1: **DBSCHEMA_TABLES**<br />2: **DBSCHEMA_COLUMNS**<br />3: **DBSCHEMA_PROVIDER_TYPES**<br />4: **MDSCHEMA_CUBES**<br />5: **MDSCHEMA_DIMENSIONS**<br />6: **MDSCHEMA_HIERARCHIES**<br />7: **MDSCHEMA_LEVELS**<br />8: **MDSCHEMA_MEASURES**<br />9: **MDSCHEMA_PROPERTIES**<br />10: **MDSCHEMA_MEMBERS**<br />11: **MDSCHEMA_FUNCTIONS**<br />12: **MDSCHEMA_ACTIONS**<br />13: **MDSCHEMA_SETS**<br />14: **DISCOVER_INSTANCES**<br />15: **MDSCHEMA_KPIS**<br />16: **MDSCHEMA_MEASUREGROUPS**<br />17: **MDSCHEMA_COMMANDS**<br />18: **DMSCHEMA_MINING_SERVICES**<br />19: **DMSCHEMA_MINING_SERVICE_PARAMETERS**<br />20: **DMSCHEMA_MINING_FUNCTIONS**<br />21: **DMSCHEMA_MINING_MODEL_CONTENT**<br />22: **DMSCHEMA_MINING_MODEL_XML**<br />23: **DMSCHEMA_MINING_MODELS**<br />24: **DMSCHEMA_MINING_COLUMNS**<br />25: **DISCOVER_DATASOURCES**<br />26: **DISCOVER_PROPERTIES**<br />27: **DISCOVER_SCHEMA_ROWSETS**<br />28: **DISCOVER_ENUMERATORS**<br />29: **DISCOVER_KEYWORDS**<br />30: **DISCOVER_LITERALS**<br />31: **DISCOVER_XML_METADATA**<br />32: **DISCOVER_TRACES**<br />33: **DISCOVER_TRACE_DEFINITION_PROVIDERINFO**<br />34: **DISCOVER_TRACE_COLUMNS**<br />35: **DISCOVER_TRACE_EVENT_CATEGORIES**<br />36: **DMSCHEMA_MINING_STRUCTURES**<br />37: **DMSCHEMA_MINING_STRUCTURE_COLUMNS**<br />38: **DISCOVER_MASTER_KEY**<br />39: **MDSCHEMA_INPUT_DATASOURCES**<br />40: **DISCOVER_LOCATIONS**<br />41: **DISCOVER_PARTITION_DIMENSION_STAT**<br />42: **DISCOVER_PARTITION_STAT**<br />43: **DISCOVER_DIMENSION_STAT**<br />44: **MDSCHEMA_MEASUREGROUP_DIMENSIONS**<br />45: **DISCOVER_XEVENT_TRACE_DEFINITION**|  
|CurrentTime|2|5|Содержит текущее время события обнаружения, если доступно. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|StartTime|3|5|Содержит время (если доступно) возникновения события окончания обнаружения. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|EndTime|4|5|Содержит время окончания события. Этот столбец не заполняется для таких классов событий запуска, как SQL:BatchStarting или SP:Starting. Ожидаемые форматы фильтрации: «ГГГГ-ММ-ДД» и «ГГГГ-ММ-ДД ЧЧ:ММ:СС».|  
|Duration|5|2|Содержит приблизительное количество времени (в миллисекундах), которое заняло событие обнаружения.|  
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
 [Категория события «События обнаружения»](discover-events-event-category.md)  
  
  
