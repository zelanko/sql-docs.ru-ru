---
title: Элемент MembersWithData (ASSL) | Документы Microsoft
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
- MembersWithData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MembersWithData
helpviewer_keywords:
- MembersWithData element
ms.assetid: 845087a2-b12d-4344-a8be-85ca61155296
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5c0311a774b225234aeb63d4d67680e12b693b0d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192308"
---
# <a name="memberswithdata-element-assl"></a>Элемент MembersWithData (ASSL)
  Определяет, следует ли отображать элементы данных для неконечных элементов в родительском атрибуте.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <MembersWithData>...</MembersWithData>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*NonLeafDataVisible*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение `MembersWithData` элемент используется только родительскими атрибутами (другими словами, значение [использование](usage-element-dimensionattribute-assl.md) элемент `DimensionAttribute` родительского элемента имеет значение *родительского*) для определения ли для отображения элементов данных для неконечных элементов в родительском атрибуте. Дополнительные сведения об элементах данных см. в разделе [Атрибуты в иерархиях типа "родители-потомки"](../../multidimensional-models/parent-child-dimension-attributes.md).  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*NonLeafDataHidden*|Неконечные данные скрыты.|  
|*NonLeafDataVisible*|Неконечные данные видимы.|  
  
 Перечисление, соответствующее допустимым значениям элемента `MembersWithData` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.MembersWithData>.  
  
## <a name="see-also"></a>См. также  
 [Элемент MembersWithDataCaption &#40;ASSL&#41;](caption-element-assl.md)   
 [Тип данных DimensionAttribute &#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  