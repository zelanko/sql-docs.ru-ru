---
title: "Элемент FontFlags (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- FontFlags Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- FontFlags
helpviewer_keywords:
- FontFlags element
ms.assetid: ea608da9-ab05-42ab-8872-c52cd9f3f546
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8dd5fc52330966160d9674d7bb89e6794cffad46
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="fontflags-element-assl"></a>Элемент FontFlags (ASSL)
  Описывает характеристики отображения шрифта [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) или [мер](../../../analysis-services/scripting/objects/measure-element-assl.md) родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
      <FontFlags>...</FontFlags>  
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
|Родительские элементы|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md), [мер](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **FontFlags** свойство содержит выражение многомерных выражений (MDX) и применяется к **CalculationProperty** элементы, которые имеют [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) из *Член* или *ячейки*.  
  
 Элементы, соответствующие родителям элемента **FontFlags** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CalculationProperty> и <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент CalculationProperties &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Элемент MdxScript &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScript, элемент &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

