---
title: "Элемент CalculationReference (ASSL) | Документы Microsoft"
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
- CalculationReference Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CalculationReference
helpviewer_keywords:
- CalculationReference element
ms.assetid: 4dd18b1f-55c3-4673-afbe-736d1bce8331
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 18df3c7f00efc4173b5651c2f2fb7528419278c3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="calculationreference-element-assl"></a>Элемент CalculationReference (ASSL)
  Содержит имя именованного набора или вычисляемой ячейки, на который указывает [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CalculationProperty>  
   ...  
   <CalculationReference>...</CalculationReference>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Если значение **CalculationReference** соответствует имени существующего именованный набор или вычисляемых ячеек, определения, **CalculationReference** учитывается.  
  
 Элемент, соответствующий родителю параметра **CalculationReference** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент CalculationProperties &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Элемент MdxScript &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScript, элемент &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

