---
title: "Элемент KeyColumn (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
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
apiname: KeyColumn Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: KeyColumn
helpviewer_keywords: KeyColumn element
ms.assetid: 7b03eeb3-d478-4c38-822e-8cdfcc485039
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 87333935a62f8aa056278ec50f01f8a45a968b91
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="keycolumn-element-assl"></a>Элемент KeyColumn (ASSL)
  Содержит определение столбца, который является ключевым или входит в состав ключа для атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<KeyColumns>  
   <KeyColumn xsi:type="DataItem">...</KeyColumn>  
<KeyColumns>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|1-N: обязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения о **DataItem** типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) и свойства **DataItem** введите см. в разделе [DataItem, тип данных &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Элементы, соответствующие родителям элемента **KeyColumns** коллекции в объектной модели Analysis Management объекты AMO <xref:Microsoft.AnalysisServices.AggregationInstanceAttribute>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, <xref:Microsoft.AnalysisServices.MeasureGroupAttribute>, и <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также:  
 [Тип данных AggregationInstanceAttribute &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationinstanceattribute-data-type-assl.md)   
 [Тип данных AggregationInstanceCubeDimension &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationinstancecubedimension-data-type-assl.md)   
 [Тип данных DimensionAttribute &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)   
 [Тип данных MeasureGroupAttribute &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)   
 [Тип данных ScalarMiningStructureColumn &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
