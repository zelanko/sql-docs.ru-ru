---
title: "Элемент AssociatedMeasureGroupID (ASSL) | Документы Microsoft"
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
apiname: AssociatedMeasureGroupID Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AssociatedMeasureGroupID
helpviewer_keywords: AssociatedMeasureGroupID element
ms.assetid: a18ff25b-00a2-4ddf-abcc-ef4d52c8a462
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3d24bfd71f9e1fd785e97737d314d9f3da6ee833
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="associatedmeasuregroupid-element-assl"></a>Элемент AssociatedMeasureGroupID (ASSL)
  Содержит идентификатор [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) элемента, связанного с [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) элемент или [ключевого показателя эффективности](../../../analysis-services/scripting/objects/kpi-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CalculationProperty> <!-- or Kpi -->  
   ...  
   <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md), [ключевого показателя эффективности](../../../analysis-services/scripting/objects/kpi-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 При применении к **CalculationProperty** элементов, **AssociatedMeasureGroupID** свойство применяется к элементам со [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) из *члена* .  
  
 Элементы, соответствующие родителям элемента **AssociatedMeasureGroupID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CalculationProperty> и <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент CalculationProperties &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Элемент MdxScript &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScript, элемент &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
