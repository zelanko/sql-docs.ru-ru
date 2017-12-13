---
title: "Набор строк DISCOVER_XML_METADATA | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DISCOVER_XML_METADATA
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_XML_METADATA rowset
ms.assetid: 0befd026-db1b-43ac-b0e6-734abb56a4b1
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ae0b5c6375fe196d780a8b13b13178157161ebfb
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="discoverxmlmetadata-rowset"></a>Набор строк DISCOVER_XML_METADATA
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Возвращает XML-документ, описывающий запрошенный объект. Возвращаемый набор строк всегда состоит из одной строки и одного столбца.  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_XML_METATDATA** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover**возвращает **DISCOVER_XML_METATDATA** набора строк.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_XML_METADATA** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
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
  
 Ограничения, **ObjectExpansion**, доступных для каждого основного объекта служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. В клиенте ограничения обычно используются для описания объектов OLAP, для которых должен быть возвращен код на языке DDL, а ограничение **ObjectExpansion** служит для определения степени развертывания в возвращаемом коде на языке DDL. Следующая таблица указывает, может ли значение перечисления для [Alter элемент &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) команд.  
  
|Значение перечисления|Description|  
|-----------------------|-----------------|  
|**ReferenceOnly**|Возвращает только имя/идентификатор/отметку времени/состояние, требуемое для запрашиваемых объектов, а также, рекурсивно, все основные объекты-потомки.|  
|**ObjectProperties**|Развертывает запрашиваемый объект без ссылок на содержащиеся объекты (включает развернутые более мелкие содержащиеся объекты).|  
|**ExpandObject**|Аналогичен параметру *ObjectProperties*, но также возвращает имя, идентификатор и отметку времени для вложенных основных объектов.|  
|**ExpandFull**|Полностью развертывает запрашиваемый объект рекурсивно до конца каждого содержащегося объекта.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
