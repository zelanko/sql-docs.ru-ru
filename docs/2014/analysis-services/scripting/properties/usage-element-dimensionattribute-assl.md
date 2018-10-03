---
title: Элемент Usage (DimensionAttribute) (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Usage Element (DimensionAttribute)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Usage
helpviewer_keywords:
- Usage element
ms.assetid: c5e38d2e-5a8e-4157-84e9-285e78c84e74
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 91c9eb328103f4d6a22a965e519836968413b43b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149324"
---
# <a name="usage-element-dimensionattribute-assl"></a>Элемент Usage (DimensionAttribute) (ASSL)
  Описывает, как используется атрибут.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
      ...  
   <Usage>...</Usage>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Регулярные*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Регулярные*|Этот атрибут является обычным атрибутом.|  
|*Key*|Этот атрибут является ключевым атрибутом.|  
|*Parent*|Этот атрибут является родительским атрибутом.|  
  
 Перечисление, соответствующее допустимым значениям элемента `Usage` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.AttributeUsage>.  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и иерархии атрибутов](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
