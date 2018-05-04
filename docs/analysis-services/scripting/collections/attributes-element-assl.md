---
title: Атрибуты элемента (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Attributes Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Attributes
helpviewer_keywords:
- Attributes element
ms.assetid: d6b545e6-1521-496f-a731-f2c2c44118e4
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 046a8ccc1f81111a5a5c0cc7012f48e26b265e5a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="attributes-element-assl"></a>Attributes, элемент (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит коллекцию атрибутов для связанного измерения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationDesignDimension> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Attributes>  
      <Attribute>...</Attribute>  
  </Attributes>  
   ...  
</AggregationDesignDimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AggregationDesignDimension](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md), [AggregationDimension](../../../analysis-services/scripting/data-type/aggregationdimension-data-type-assl.md), [AggregationInstanceCubeDimension](../../../analysis-services/scripting/data-type/aggregationinstancecubedimension-data-type-assl.md), [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md), [измерения ](../../../analysis-services/scripting/objects/dimension-element-assl.md), [PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md), [RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md), [RelationshipEnd](../../../analysis-services/scripting/data-type/relationshipend-data-type-assl.md)|  
|Дочерние элементы|[Атрибут](../../../analysis-services/scripting/objects/attribute-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующими элементами в модели объектов AMO являются <xref:Microsoft.AnalysisServices.AggregationAttributeCollection>, <xref:Microsoft.AnalysisServices.AggregationDesignAttributeCollection>, <xref:Microsoft.AnalysisServices.AggregationInstanceAttributeCollection>, <xref:Microsoft.AnalysisServices.CubeAttributeCollection>, <xref:Microsoft.AnalysisServices.DimensionAttributeCollection>, <xref:Microsoft.AnalysisServices.MeasureGroupAttributeCollection> и <xref:Microsoft.AnalysisServices.PerspectiveAttributeCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
