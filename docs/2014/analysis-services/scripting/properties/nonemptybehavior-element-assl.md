---
title: Элемент NonEmptyBehavior (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- NonEmptyBehavior Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NonEmptyBehavior
helpviewer_keywords:
- NonEmptyBehavior element
ms.assetid: b4c78af4-b049-4189-a35b-206e3938d1db
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d328b41ee8c40497019fe918d40925b3ce2a1436
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180127"
---
# <a name="nonemptybehavior-element-assl"></a>Элемент NonEmptyBehavior (ASSL)
  Определяет установленное поведение, связанное с родителем элемента [CalculationProperty](../objects/calculationproperty-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CalculationProperty>  
  
   <NonEmptyBehavior>...</NonEmptyBehavior>  
  
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
|Родительский элемент|[CalculationProperty](../objects/calculationproperty-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 `NonEmptyBehavior` Свойство применяется к `CalculationProperty` элементы с [CalculationType](calculationtype-element-assl.md) значение *член*.  
  
 Элемент, соответствующий родителю параметра `NonEmptyBehavior` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CalculationProperties &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  