---
title: Элемент CalculationType (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d295ec471039d6f4853c8c0fb1eab730d11d69b1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="calculationtype-element-assl"></a>Элемент CalculationType (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Описывает тип вычисления, определенный в связанном [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CalculationProperty>  
   ...  
   <CalculationType>...</CalculationType>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Член*|Областью применения свойства вычисления является определение вычисляемого элемента.|  
|*Набор*|Областью применения свойства вычисления является определение именованного набора.|  
|*Ячейки*|Областью применения свойства вычисления является определение вычисляемой ячейки.|  
  
 Перечисление, соответствующее разрешенным значениям для **CalculationType** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CalculationType>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CalculationProperties &#40;ASSL&#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
