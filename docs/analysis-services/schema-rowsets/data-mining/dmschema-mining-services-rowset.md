---
title: "Набор строк DMSCHEMA_MINING_SERVICES | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DMSCHEMA_MINING_SERVICES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICES rowset
ms.assetid: 4a672f2f-d637-4def-a572-c18556f83d34
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7e7a9f2cd1d082bd2c33a15c66ce9b3fb170eb9e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dmschemaminingservices-rowset"></a>Набор строк DMSCHEMA_MINING_SERVICES
  Содержит описание всех алгоритмов интеллектуального анализа данных, поддерживаемых поставщиком.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **DMSCHEMA_MINING_SERVICES** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Description|  
|-----------------|--------------------|-----------------|  
|**ПАРАМЕТРЫ SERVICE_NAME**|**DBTYPE_WSTR**|Имя алгоритма. Столбцы относятся к конкретным поставщикам.|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|Этот столбец содержит битовую карту, описывающую службу интеллектуального анализа данных. [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] помещает в него одно из следующих значений:<br /><br /> **DM_SERVICETYPE_CLASSIFICATION** (**1**)<br /><br /> **DM_SERVICETYPE_CLUSTERING** (**2**)|  
|**SERVICE_DISPLAY_NAME**|**DBTYPE_WSTR**|Локализуемое отображаемое имя алгоритма.|  
|**SERVICE_GUID**|**DBTYPE_GUID**|Идентификатор GUID алгоритма.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Понятное описание алгоритма.|  
|**PREDICTION_LIMIT**|**DBTYPE_UI4**|Максимальное число прогнозов, которое могут предоставить модель и алгоритм.|  
|**SUPPORTED_DISTRIBUTION_FLAGS**|**DBTYPE_WSTR**|Список флагов (с разделителями-запятыми), описывающий статистическое распределение, поддерживаемое алгоритмом. Этот столбец содержит одно или несколько из следующих значений.<br /><br /> «**ОБЫЧНЫЙ**»<br /><br /> «**ОБЫЧНЫЙ ЖУРНАЛА**»<br /><br /> «**УНИВЕРСАЛЬНЫЙ**»|  
|**SUPPORTED_INPUT_CONTENT_TYPES**|**DBTYPE_WSTR**|Список флагов (с разделителями-запятыми), описывающий типы входного содержимого, поддерживаемые алгоритмом. Этот столбец содержит одно или несколько из следующих значений.<br /><br /> «**КЛЮЧ**»<br /><br /> «**DISCRETE**»<br /><br /> «**CONTINUOUS**»<br /><br /> «**DISCRETIZED**»<br /><br /> «**ORDERED**»<br /><br /> «КЛЮЧ **ПОСЛЕДОВАТЕЛЬНОСТИ**»<br /><br /> «**CYCLICAL**»<br /><br /> «**ВЕРОЯТНОСТЬ**»<br /><br /> «**ДИСПЕРСИЮ**»<br /><br /> «**STDEV**»<br /><br /> «**ПОДДЕРЖКИ**»<br /><br /> «**ДИСПЕРСИЮ ВЕРОЯТНОСТИ**»<br /><br /> «**STDEV ВЕРОЯТНОСТИ**»<br /><br /> «**КЛЮЧЕВОЙ СТОЛБЕЦ ВРЕМЕНИ**»|  
|**SUPPORTED_PREDICTION_CONTENT_TYPES**|**DBTYPE_WSTR**|Список флагов (с разделителями-запятыми), описывающий типы входного содержимого прогнозов, поддерживаемые алгоритмом. Этот столбец содержит одно или несколько из следующих значений.<br /><br /> «**КЛЮЧ**»<br /><br /> «**DISCRETE**»<br /><br /> «**CONTINUOUS**»<br /><br /> «**DISCRETIZED**»<br /><br /> «**ORDERED**»<br /><br /> «КЛЮЧ **ПОСЛЕДОВАТЕЛЬНОСТИ** »<br /><br /> «**CYCLICAL**»<br /><br /> «**ВЕРОЯТНОСТЬ**»<br /><br /> «**ДИСПЕРСИЮ**»<br /><br /> «**STDEV**»<br /><br /> «**ПОДДЕРЖКИ**»<br /><br /> «**ДИСПЕРСИЮ ВЕРОЯТНОСТИ**»<br /><br /> «**STDEV ВЕРОЯТНОСТИ**»<br /><br /> "KEY TIME"|  
|**SUPPORTED_MODELING_FLAGS**|**DBTYPE_WSTR**|Список флагов моделирования (с разделителями-запятыми), поддерживаемых алгоритмом. Этот столбец содержит одно или несколько из следующих значений.<br /><br /> «**MODEL_EXISTENCE_ONLY**»<br /><br /> «**РЕГРЕССОРА**»<br /><br /> <br /><br /> Обратите внимание, что также можно определить флаги для конкретных поставщиков.|  
|**SUPPORTED_SOURCE_QUERY**|**DBTYPE_WSTR**|Этот столбец поддерживается для обеспечения обратной совместимости.|  
|**TRAINING_COMPLEXITY**|**DBTYPE_I4**|Предполагаемая продолжительность обучения.<br /><br /> **DM_TRAINING_COMPLEXITY_LOW** указывает короткое время выполнения и пропорционально объему входных данных.<br /><br /> **DM_TRAINING_COMPLEXITY_MEDIUM** указывает, что время выполнения может быть много, но обычно пропорционально объему входных данных.<br /><br /> **DM_TRAINING_COMPLEXITY_HIGH** указывает, что время выполнения велико, и он может расти экспоненциально число обучающих вариантов.|  
|**PREDICTION_COMPLEXITY**|**DBTYPE_I4**|Предполагаемая продолжительность прогноза:<br /><br /> **DM_PREDICTION_COMPLEXITY_LOW** указывает короткое время выполнения и пропорционально объему входных данных.<br /><br /> **DM_PREDICTION_COMPLEXITY_MEDIUM** указывает, что время выполнения может быть много, но обычно пропорционально объему входных данных.<br /><br /> **DM_PREDICTION_COMPLEXITY_HIGH** указывает, что время выполнения велико, и он может расти экспоненциально число обучающих вариантов.|  
|**EXPECTED_QUALITY**|**DBTYPE_I4**|Ожидаемое качество модели, создаваемой этим алгоритмом.<br /><br /> **DM_EXPECTED_QUALITY_LOW**<br /><br /> **DM_EXPECTED_QUALITY_MEDIUM**<br /><br /> **DM_EXPECTED_QUALITY_HIGH**|  
|**МАСШТАБИРОВАНИЕ**|**DBTYPE_I4**|Масштабируемость алгоритма.<br /><br /> **DM_SCALING_LOW**<br /><br /> **DM_SCALING_MEDIUM**<br /><br /> **DM_SCALING_HIGH**|  
|**ALLOW_INCREMENTAL_INSERT**|**DBTYPE_BOOL**|Логическое значение. Указывает, поддерживает ли алгоритм добавочное обучение, т. е. обновление обнаруженных закономерностей на основе новых фактических данных, а не полное повторное обнаружение закономерностей.|  
|**ALLOW_PMML_INITIALIZATION**|**DBTYPE_BOOL**|Логическое значение. Показывает, можно ли создавать модели интеллектуального анализа данных на основе строки PMML 2.1.<br /><br /> Если **TRUE**, алгоритм интеллектуального анализа данных поддерживает инициализацию из содержимого PMML 2.1.|  
|**ЭЛЕМЕНТ УПРАВЛЕНИЯ**|**DBTYPE_I4**|Предоставляемая поддержка при прерванном обучении.<br /><br /> **DM_CONTROL_NONE** указывает, что алгоритм не может быть отменено после его запуска для обучения модели.<br /><br /> **DM_CONTROL_CANCEL** указывает, что алгоритма можно отменить после он начнет обучать модель, но необходимо перезагрузить для возобновления обучения.<br /><br /> **DM_CONTROL_SUSPENDRESUME** указывает алгоритма можно отменять и возобновлять в любое время, но результаты будут доступны до завершения обучения.<br /><br /> **DM_CONTROL_SUSPENDWITHRESULT** указывает алгоритма можно отменять и возобновлять в любое время, которое можно получить результаты.|  
|**ALLOW_DUPLICATE_KEY**|**DBTYPE_BOOL**|Логическое значение. Показывает, могут ли варианты содержать повторяющиеся ключи.<br /><br /> Если **VARIANT_TRUE**, варианты могут содержать повторяющиеся ключи.|  
|**VIEWER_TYPE**|**DBTYPE_WSTR**|Рекомендуемое средство просмотра для данной модели.|  
|**HELP_FILE**|**DBTYPE_WSTR**|Имя файла с документацией по этой службе (необязательно).|  
|**HELP_CONTEXT**|**DBTYPE_I4**|Идентификатор контекста справки для этой службы (необязательно).|  
|**MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL**|**DBTYPE_WSTR**|Поддерживаемая версия DDL. «0» означает, что DDL не поддерживается.|  
|**MSOLAP_SUPPORTS_OLAP_MINING_MODELS**|**DBTYPE_BOOL**|Логическое значение. Показывает, можно ли создавать модели интеллектуального анализа OLAP.<br /><br /> Если **TRUE**, модели интеллектуального анализа данных OLAP могут быть созданы. Требуется **MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL** должно быть не равно нулю.|  
|**MSOLAP_SUPPORTS_DATA_MINING_DIMENSIONS**|**DBTYPE_BOOL**|Логическое значение. Показывает, можно ли создавать измерения интеллектуального анализа данных.<br /><br /> Если **TRUE**, могут быть созданы измерения интеллектуального анализа данных.|  
|**MSOLAP_SUPPORTS_DRILLTHROUGH**|**DBTYPE_BOOL**|Логическое значение. Показывает, поддерживает ли служба возможности детализации.<br /><br /> Если **TRUE**, что служба поддерживает возможности детализации.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **DMSCHEMA_MINING_SERVICES** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**ПАРАМЕТРЫ SERVICE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|Необязательно.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы интеллектуального анализа данных](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  

