---
title: Элемент FontSize (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- FontSize Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- FontSize
helpviewer_keywords:
- FontSize element
ms.assetid: 49f66a73-946a-4fbd-9749-a3ca1b717ff3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8486b3b6404b9518f4fa099fa5bdb821f74c1ed2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178114"
---
# <a name="fontsize-element-assl"></a>Элемент FontSize ASSL)
  Описывает характеристики отображения, связанные со шрифтами [CalculationProperty](../objects/calculationproperty-element-assl.md) или [мер](../objects/measure-element-assl.md) родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <FontSize>...</FontSize>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CalculationProperty](../objects/calculationproperty-element-assl.md), [мер](../objects/measure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 `FontSize` Содержит выражение многомерных выражений (MDX) и применяется к `CalculationProperty` элементов, которые имеют [CalculationType](calculationtype-element-assl.md) из *член* или *ячеек* .  
  
 Элементы, соответствующие родителям элемента `FontSize` в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.CalculationProperty> и <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CalculationProperties &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Элемент MdxScripts &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
