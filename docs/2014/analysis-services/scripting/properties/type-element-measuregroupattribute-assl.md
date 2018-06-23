---
title: Введите элемент (MeasureGroupAttribute) (ASSL) | Документы Microsoft
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
- Type Element (MeasureGroupAttribute)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 93740504-297a-4a06-ab3e-b598e466eebb
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0d06b5df3ba99e54ec62de5c6f274874289cbbc4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101832"
---
# <a name="type-element-measuregroupattribute-assl"></a>Элемент Type (MeasureGroupAttribute) (ASSL)
  Содержит тип [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroupAttribute>  
   ...  
   <Type>...</Type>  
   ...  
</MeasureGroupAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Обычный*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Обычный*|Представляет обычный атрибут.|  
|*Гранулярность*|Представляет атрибут гранулярности.|  
  
 Перечисление, соответствующее допустимым значениям элемента `Type` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.MeasureGroupAttributeType>.  
  
 Элемент, соответствующий родителю параметра `Type` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MeasureGroupAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Атрибуты элемента &#40;ASSL&#41;](../collections/attributes-element-assl.md)   
 [Тип данных RegularMeasureGroupDimension &#40;ASSL&#41;](../data-type/dimension-data-type-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  