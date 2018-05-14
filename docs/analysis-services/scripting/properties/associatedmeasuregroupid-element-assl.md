---
title: Элемент AssociatedMeasureGroupID (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0b74c0160e592372cb6fd2d2674cd2eec13a4582
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="associatedmeasuregroupid-element-assl"></a>Элемент AssociatedMeasureGroupID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md), [ключевого показателя эффективности](../../../analysis-services/scripting/objects/kpi-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 При применении к **CalculationProperty** элементов, **AssociatedMeasureGroupID** свойство применяется к элементам со [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) из *члена* .  
  
 Элементы, соответствующие родителям элемента **AssociatedMeasureGroupID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CalculationProperty> и <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CalculationProperties &#40;ASSL&#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
