---
title: Набор строк DMSCHEMA_MINING_SERVICES | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_SERVICES
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICES rowset
ms.assetid: 4a672f2f-d637-4def-a572-c18556f83d34
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b268abe234c8df71672ca434494ee89717a15947
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087002"
---
# <a name="dmschemaminingservices-rowset"></a>Набор строк DMSCHEMA_MINING_SERVICES
  Содержит описание всех алгоритмов интеллектуального анализа данных, поддерживаемых поставщиком.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DMSCHEMA_MINING_SERVICES` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Имя алгоритма. Столбцы относятся к конкретным поставщикам.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`||Этот столбец содержит битовую карту, описывающую службу интеллектуального анализа данных. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Помещает в него одно из следующих значений:<br /><br /> -   `DM_SERVICETYPE_CLASSIFICATION` (`1`)<br />-   `DM_SERVICETYPE_CLUSTERING` (`2`)|  
|`SERVICE_DISPLAY_NAME`|`DBTYPE_WSTR`||Локализуемое отображаемое имя алгоритма.|  
|`SERVICE_GUID`|`DBTYPE_GUID`||Идентификатор GUID алгоритма.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание алгоритма.|  
|`PREDICTION_LIMIT`|`DBTYPE_UI4`||Максимальное число прогнозов, которое могут предоставить модель и алгоритм.|  
|`SUPPORTED_DISTRIBUTION_FLAGS`|`DBTYPE_WSTR`||Список флагов (с разделителями-запятыми), описывающий статистическое распределение, поддерживаемое алгоритмом. Этот столбец содержит одно или несколько из следующих значений.<br /><br /> -   "`NORMAL`"<br />-   "`LOG NORMAL`"<br />-   "`UNIFORM`"|  
|`SUPPORTED_INPUT_CONTENT_TYPES`|`DBTYPE_WSTR`||Список флагов (с разделителями-запятыми), описывающий типы входного содержимого, поддерживаемые алгоритмом. Этот столбец содержит одно или несколько из следующих значений.<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-   "`DISCRETIZED`"<br />-   "`ORDERED`"<br />-«КЛЮЧ `SEQUENCE`»<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY VARIANCE`"<br />-   "`PROBABILITY STDEV`"<br />-   "`KEY TIME`"|  
|`SUPPORTED_PREDICTION_CONTENT_TYPES`|`DBTYPE_WSTR`||Список флагов (с разделителями-запятыми), описывающий типы входного содержимого прогнозов, поддерживаемые алгоритмом. Этот столбец содержит одно или несколько из следующих значений.<br /><br /> -   "`KEY`"<br />-   "`DISCRETE`"<br />-   "`CONTINUOUS`"<br />-   "`DISCRETIZED`"<br />-   "`ORDERED`"<br />-«КЛЮЧ `SEQUENCE` »<br />-   "`CYCLICAL`"<br />-   "`PROBABILITY`"<br />-   "`VARIANCE`"<br />-   "`STDEV`"<br />-   "`SUPPORT`"<br />-   "`PROBABILITY VARIANCE`"<br />-   "`PROBABILITY STDEV`"<br />-«KEY TIME»|  
|`SUPPORTED_MODELING_FLAGS`|`DBTYPE_WSTR`||Список флагов моделирования (с разделителями-запятыми), поддерживаемых алгоритмом. Этот столбец содержит одно или несколько из следующих значений.<br /><br /> -   "`MODEL_EXISTENCE_ONLY`"<br />-   "`REGRESSOR`"<br /><br /> Также могут определяться флаги для конкретных поставщиков.|  
|`SUPPORTED_SOURCE_QUERY`|`DBTYPE_WSTR`||-Этот столбец поддерживается для обеспечения обратной совместимости.|  
|`TRAINING_COMPLEXITY`|`DBTYPE_I4`||Предполагаемая продолжительность обучения.<br /><br /> -   `DM_TRAINING_COMPLEXITY_LOW` Указывает, короткое время выполнения и пропорционально объему входных данных.<br />-   **DM_TRAINING_COMPLEXITY_MEDIUM** указывает, что время выполнения может быть много, но обычно пропорционально объему входных данных.<br />-   **DM_TRAINING_COMPLEXITY_HIGH** указывает, что время выполнения велико, и он может расти экспоненциально число обучающих вариантов.|  
|`PREDICTION_COMPLEXITY`|`DBTYPE_I4`||Предполагаемая продолжительность прогноза:<br /><br /> -   **DM_PREDICTION_COMPLEXITY_LOW** указывает короткое время выполнения и пропорционально объему входных данных.<br />-   **DM_PREDICTION_COMPLEXITY_MEDIUM** указывает, что время выполнения может быть много, но обычно пропорционально объему входных данных.<br />-   **DM_PREDICTION_COMPLEXITY_HIGH** указывает, что время выполнения велико, и он может расти экспоненциально число обучающих вариантов.|  
|`EXPECTED_QUALITY`|`DBTYPE_I4`||Ожидаемое качество модели, создаваемой этим алгоритмом.<br /><br /> -   `DM_EXPECTED_QUALITY_LOW`<br />-   `DM_EXPECTED_QUALITY_MEDIUM`<br />-   **DM_EXPECTED_QUALITY_HIGH**|  
|`SCALING`|`DBTYPE_I4`||Масштабируемость алгоритма.<br /><br /> -   **DM_SCALING_LOW**<br />-   `DM_SCALING_MEDIUM`<br />-   **DM_SCALING_HIGH**|  
|`ALLOW_INCREMENTAL_INSERT`|`DBTYPE_BOOL`||Логическое значение. Указывает, поддерживает ли алгоритм добавочное обучение, т. е. обновление обнаруженных закономерностей на основе новых фактических данных, а не полное повторное обнаружение закономерностей.|  
|`ALLOW_PMML_INITIALIZATION`|`DBTYPE_BOOL`||Логическое значение. Показывает, можно ли создавать модели интеллектуального анализа данных на основе строки PMML 2.1.<br /><br /> Если значение равно `TRUE`, то алгоритм интеллектуального анализа данных поддерживает инициализацию из содержимого PMML 2.1.|  
|`CONTROL`|`DBTYPE_I4`||Предоставляемая поддержка при прерванном обучении.<br /><br /> -   `DM_CONTROL_NONE` Указывает, что алгоритм не может быть отменено после его запуска для обучения модели.<br />-   `DM_CONTROL_CANCEL` Указывает, что алгоритм может быть отменено после он начнет обучать модель, но для возобновления обучения необходимо перезапустить.<br />-   `DM_CONTROL_SUSPENDRESUME` Указывает, что алгоритма можно отменять и возобновлять в любое время, но результаты будут доступны до завершения обучения.<br />-   `DM_CONTROL_SUSPENDWITHRESULT` Указывает, что алгоритма можно отменять и возобновлять в любое время, и результаты могут быть получены.|  
|`ALLOW_DUPLICATE_KEY`|`DBTYPE_BOOL`||Логическое значение. Показывает, могут ли варианты содержать повторяющиеся ключи.<br /><br /> Если значение равно `VARIANT_TRUE`, то варианты могут содержать повторяющиеся ключи.|  
|`VIEWER_TYPE`|`DBTYPE_WSTR`||Рекомендуемое средство просмотра для данной модели.|  
|`HELP_FILE`|`DBTYPE_WSTR`||Имя файла с документацией по этой службе (необязательно).|  
|`HELP_CONTEXT`|`DBTYPE_I4`||Идентификатор контекста справки для этой службы (необязательно).|  
|`MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL`|`DBTYPE_WSTR`||Поддерживаемая версия DDL. «0» означает, что DDL не поддерживается.|  
|`MSOLAP_SUPPORTS_OLAP_MINING_MODELS`|`DBTYPE_BOOL`||Логическое значение. Показывает, можно ли создавать модели интеллектуального анализа OLAP.<br /><br /> Если значение равно `TRUE`, то модели интеллектуального анализа OLAP создавать можно. Для этого требуется, чтобы значение параметра `MSOLAP_SUPPORTS_ANALYSIS_SERVICES_DDL` было отличным от нуля.|  
|`MSOLAP_SUPPORTS_DATA_MINING_DIMENSIONS`|`DBTYPE_BOOL`||Логическое значение. Показывает, можно ли создавать измерения интеллектуального анализа данных.<br /><br /> Если значение равно `TRUE`, то измерения интеллектуального анализа данных создавать можно.|  
|`MSOLAP_SUPPORTS_DRILLTHROUGH`|`DBTYPE_BOOL`||Логическое значение. Показывает, поддерживает ли служба возможности детализации.<br /><br /> Если значение равно `TRUE`, то служба поддерживает возможности детализации.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DMSCHEMA_MINING_SERVICES` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы интеллектуального анализа данных](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  