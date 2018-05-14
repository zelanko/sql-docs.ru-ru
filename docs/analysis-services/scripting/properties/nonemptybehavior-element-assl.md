---
title: Элемент NonEmptyBehavior (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 41dbb603f97adde99d033a50c81ae15686bb7618
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="nonemptybehavior-element-assl"></a>Элемент NonEmptyBehavior (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет установленное поведение, связанное с родителем элемента [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CalculationProperty>  
  
   <NonEmptyBehavior>...</NonEmptyBehavior>  
  
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
|Родительский элемент|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **NonEmptyBehavior** свойство применяется к **CalculationProperty** элементы с [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) значение *член*.  
  
 Элемент, соответствующий родителю параметра **NonEmptyBehavior** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CalculationProperties &#40;ASSL&#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
