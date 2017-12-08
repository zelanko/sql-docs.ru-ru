---
title: "Атрибут элемента (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Attribute Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Attribute
helpviewer_keywords: Attribute element
ms.assetid: 079ec9f8-a314-4e3c-821a-b42c65cc7363
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6a4586966f0718bc3108bf000356901982308bbd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="attribute-element-assl"></a>Элемент Attribute (ASSL)
  Содержит описание атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Attributes>  
   <Attribute xsi:type="AggregationAttribute">...</Attribute> <!-- ancestor: AggregationDimension -->  
   <!-- or -->  
   <Attribute xsi:type="AggregationDesignAttribute">...</Attribute> <!-- ancestor: AggregationDesignDimension -->  
   <!-- or -->  
   <Attribute xsi:type="AggregationInstanceAttribute">...</Attribute> <!-- ancestor: AggregationInstanceCubeDimension -->  
   <!-- or -->  
   <Attribute xsi:type="CubeAttribute">...</Attribute> <!--ancestor:  CubeDimension -->  
   <!-- or -->  
   <Attribute xsi:type="DimensionAttribute">...</Attribute> <!-- ancestor: Dimension -->  
   <!-- or -->  
   <Attribute xsi:type="MeasureGroupAttribute">...</Attribute> <!-- ancestor: RegularMeasureGroupDimension -->  
   <!-- or -->  
   <Attribute xsi:type="PerspectiveAttribute">...</Attribute> <!-- ancestor: PerspectiveDimension -->  
   <!-- or -->  
   <Attribute>  
      <AttributeID>...</AttributeID>  
   </Attribute> <!-- ancestor: RelationshipEnd -->  
</Attributes>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|См. в следующей таблице.|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
|Предок или родитель|Тип данных|  
|------------------------|---------------|  
|[AggregationDesignDimension](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md)|[AggregationDesignAttribute](../../../analysis-services/scripting/data-type/aggregationdesignattribute-data-type-assl.md)|  
|[AggregationDimension](../../../analysis-services/scripting/data-type/aggregationdimension-data-type-assl.md)|[AggregationAttribute](../../../analysis-services/scripting/data-type/aggregationattribute-data-type-assl.md)|  
|[AggregationInstanceCubeDimension](../../../analysis-services/scripting/data-type/aggregationinstancecubedimension-data-type-assl.md)|[AggregationInstanceAttribute](../../../analysis-services/scripting/data-type/aggregationinstanceattribute-data-type-assl.md)|  
|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md)|  
|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|[RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md)|[MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)|  
|[PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md)|[PerspectiveAttribute](../../../analysis-services/scripting/data-type/perspectiveattribute-data-type-assl.md)|  
|[RelationshipEnd](../../../analysis-services/scripting/data-type/relationshipend-data-type-assl.md)|\<Атрибут ><br />      \<[AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)>... \</AttributeID > \< /атрибут >|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Атрибуты](../../../analysis-services/scripting/collections/attributes-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Соответствующие элементы в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AggregationDesignAttribute>, <xref:Microsoft.AnalysisServices.AggregationAttribute>, <xref:Microsoft.AnalysisServices.CubeAttribute>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, <xref:Microsoft.AnalysisServices.MeasureGroupAttribute>, и <xref:Microsoft.AnalysisServices.PerspectiveAttribute>.  
  
## <a name="see-also"></a>См. также:  
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
