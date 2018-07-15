---
title: Элемент FontName (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- FontName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- FontName
helpviewer_keywords:
- FontName element
ms.assetid: 5560a852-9745-4abb-93d8-9cebe8a9897c
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d1b179415e7b64c4d64090df6168fcc492ab1c30
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289530"
---
# <a name="fontname-element-assl"></a>Элемент FontName (ASSL)
  Описывает характеристики отображения, связанные со шрифтами [CalculationProperty](../objects/calculationproperty-element-assl.md) или [мер](../objects/measure-element-assl.md) родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <FontName>...</FontName>  
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
 `FontName` Содержит выражение многомерных выражений (MDX) и применяется к `CalculationProperty` элементов, которые имеют [CalculationType](calculationtype-element-assl.md) из *член* или *ячеек *.  
  
 Элементы, соответствующие родителям элемента `FontName` в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.CalculationProperty> и <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CalculationProperties &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Элемент MdxScripts &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
