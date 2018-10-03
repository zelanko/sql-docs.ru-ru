---
title: Набор строк DMSCHEMA_MINING_MODELS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DMSCHEMA_MINING_MODELS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODELS rowset
ms.assetid: 1636f4cf-b342-4e2e-93b4-04136e2d41ef
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 915a4f98c319af16daff2d07667463d2ec77c50d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178104"
---
# <a name="dmschemaminingmodels-rowset"></a>Набор строк DMSCHEMA_MINING_MODELS
  Перечисляет модели интеллектуального анализа данных в текущем каталоге. В набор строк `DMSCHEMA_MINING_MODELS` могут быть включены такие сведения, как имена, типы и алгоритмы интеллектуального анализа данных, связанные со всеми моделями.  
  
 . `DMSCHEMA_MINING_MODELS` Набора строк схемы очень похожа на [DBSCHEMA_TABLES](../ole-db/dbschema-tables-rowset.md) набора строк схемы и может использоваться так же.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DMSCHEMA_MINING_MODELS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Имя каталога. Заполняется именем базы данных, элементом которой является модель.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Неполное имя схемы. Этот столбец не поддерживается службами [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Имя модели интеллектуального анализа данных. Этот столбец содержит имя модели интеллектуального анализа данных и никогда не бывает пустым.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`||Тип модели.|  
|`MODEL_GUID`|`DBTYPE_GUID`||Идентификатор GUID модели.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание модели.|  
|`MODEL_PROPID`|`DBTYPE_UI4`||Идентификатор свойства модели. Этот столбец не поддерживается службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и всегда содержит значение `NULL`.|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||Дата создания этой модели.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Дата последнего изменения определения этой модели.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`||Перечисление, определяющее тип алгоритма интеллектуального анализа данных, который используется моделью. Этот тип может иметь одно из следующих значений.<br /><br /> -   `DM_SERVICETYPE_CLASSIFICATION` (1)<br />-   `DM_SERVICETYPE_SEGMENTATION`(2)<br />-   `DM_SERVICETYPE_ ASSOCIATION`(4)<br />-   `DM_SERVICETYPE_ DENSITY_ESTIMATE`(8)<br />-   `DM_SERVICETYPE_SEQUENCE`(16)|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||Имя алгоритма интеллектуального анализа данных (для конкретного поставщика), который используется моделью.|  
|`CREATION_STATEMENT`|`DBTYPE_WSTR`||Инструкция, с помощью которой была создана модель интеллектуального анализа данных.|  
|`PREDICTION_ENTITY`|`DBTYPE_WSTR`||Список столбцов (с запятыми в качестве разделителей), для которых доступно прогнозирование.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Логический флаг. Показывает, заполняется ли модель.<br /><br /> Значение `TRUE`, если модель заполнена. В противном случае — значение `FALSE`.|  
|`MINING_PARAMETERS`|`DBTYPE_WSTR`||Список параметров с разделителями-запятыми, которые изначально использовались при создании модели.|  
|`MINING_STRUCTURE`|`DBTYPE_WSTR`||Идентификатор структуры интеллектуального анализа данных, на основе которой создана модель.|  
|`LAST_PROCESSED`|`DBTYPE_DBTIMESTAMP`||Дата и время последней обработки модели.|  
|`MSOLAP_IS_DRILLTHROUGH_ENABLED`|`DBTYPE_BOOL`||Логический флаг. Показывает, поддерживает ли модель детализацию.|  
|`FILTER`|`DBTYPE_WSTR`||Критерий фильтра, связанный с моделью интеллектуального анализа данных.<br /><br /> Значение NULL или пустая строка означают, что фильтр не применяется.|  
|`TRAINING_SET_SIZE`|`DBTYPE_UIS`||Число вариантов в обучающем наборе модели интеллектуального анализа данных после обработки структуры и применения к модели фильтров.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DMSCHEMA_MINING_MODELS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SERVICE_TYPE_ID`|`DBTYPE_UI4`|Необязательный параметр.|  
|`MINING_STRUCTURE`|`DBTYPE_WSTR`|Необязательный параметр.|  
  
 Примеры для запроса этот набор строк, см. в разделе [запрос параметров, используемых для создания модели интеллектуального анализа данных](../../data-mining/query-the-parameters-used-to-create-a-mining-model.md).  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы интеллектуального анализа данных](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
