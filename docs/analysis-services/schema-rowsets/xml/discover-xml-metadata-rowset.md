---
title: Набор строк DISCOVER_XML_METADATA | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 74b0c33570c9a7f6889e9754eeac7426f72c98ac
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="discoverxmlmetadata-rowset"></a>Набор строк DISCOVER_XML_METADATA
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Возвращает XML-документ с описанием запрошенного объекта. Возвращаемый набор строк всегда состоит из одной строки и одного столбца.  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_XML_METATDATA** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover**возвращает **DISCOVER_XML_METATDATA** набора строк.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_XML_METADATA** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**МЕТАДАННЫЕ**|**DBTYPE_WSTR**||XML-документ, который описывает объект, требуемый в соответствии с ограничением.|  
  
 Этот набор строк схемы не отсортирован.  
  
> [!IMPORTANT]  
>  Набор строк **DISCOVER_XML_METADATA** нельзя запрашивать с помощью синтаксиса команды SELECT. Тем не менее **DISCOVER_XML_METADATA** набора строк можно запрашивать с помощью <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_XML_METADATA** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**DatabaseID**|**DBTYPE_WSTR**|Необязательно.|  
|**DimensionID**|**DBTYPE_WSTR**|Необязательно.|  
|**CubeID**|**DBTYPE_WSTR**|Необязательно.|  
|**MeasureGroupID**|**DBTYPE_WSTR**|Необязательно.|  
|**PartitionID**|**DBTYPE_WSTR**|Необязательно.|  
|**PerspectiveID**|**DBTYPE_WSTR**|Необязательно.|  
|**DimensionPermissionID**|**DBTYPE_WSTR**|Необязательно.|  
|**RoleID**|**DBTYPE_WSTR**|Необязательно.|  
|**DatabasePermissionID**|**DBTYPE_WSTR**|Необязательно.|  
|**MiningModelID**|**DBTYPE_WSTR**|Необязательно.|  
|**MiningModelPermissionID**|**DBTYPE_WSTR**|Необязательно.|  
|**DataSourceID**|**DBTYPE_WSTR**|Необязательно.|  
|**MiningStructureID**|**DBTYPE_WSTR**|Необязательно.|  
|**AggregationDesignID**|**DBTYPE_WSTR**|Необязательно.|  
|**Числовое обозначение TraceID**|**DBTYPE_WSTR**|Необязательно.|  
|**MiningStructurePermissionID**|**DBTYPE_WSTR**|Необязательно.|  
|**CubePermissionID**|**DBTYPE_WSTR**|Необязательно.|  
|**Идентификатор сборки**|**DBTYPE_WSTR**|Необязательно.|  
|**MdxScriptID**|**DBTYPE_WSTR**|Необязательно.|  
|**DataSourceViewID**|**DBTYPE_WSTR**|Необязательно.|  
|**DataSourcePermissionID**|**DBTYPE_WSTR**|Необязательно.|  
|**ObjectExpansion**|**DBTYPE_WSTR**|Необязательно.|  
  
 Ограничения, **ObjectExpansion**, доступных для каждого основного объекта служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. В клиенте ограничения обычно используются для описания объектов OLAP, для которых должен быть возвращен код на языке DDL, а ограничение **ObjectExpansion** служит для определения степени развертывания в возвращаемом коде на языке DDL. Следующая таблица указывает, может ли значение перечисления для [Alter элемент &#40;XMLA&#41; ](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) команд.  
  
|Значение перечисления|Описание|  
|-----------------------|-----------------|  
|**ReferenceOnly**|Возвращает только имя/идентификатор/отметку времени/состояние, требуемое для запрашиваемых объектов, а также, рекурсивно, все основные объекты-потомки.|  
|**ObjectProperties**|Развертывает запрашиваемый объект без ссылок на содержащиеся объекты (включает развернутые более мелкие содержащиеся объекты).|  
|**ExpandObject**|Аналогичен параметру *ObjectProperties*, но также возвращает имя, идентификатор и отметку времени для вложенных основных объектов.|  
|**ExpandFull**|Полностью развертывает запрашиваемый объект рекурсивно до конца каждого содержащегося объекта.|  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
