---
title: Элемент OrderBy (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- OrderBy Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- OrderBy
helpviewer_keywords:
- OrderBy element
ms.assetid: d7a0564b-430e-44eb-913a-fe1f98917d0f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 95ed1ce8e5b9df8340b41b8ec24e713dae9739ab
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168734"
---
# <a name="orderby-element-assl"></a>Элемент OrderBy (ASSL)
  Описывает, как упорядочивать элементы, содержащиеся в атрибуте.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <OrderBy>...</OrderBy>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Название*|  
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
|*Название*|Упорядочить по имени элемента.|  
|*Key*|Упорядочить по ключу элемента.|  
|*AttributeKey*|Упорядочить по ключу элемента атрибута, заданного в [OrderByAttributeID](id-element-assl.md) элемент `DimensionAttribute`.|  
|*AttributeName*|Упорядочить по имени элемента атрибута, заданного в элементе `OrderByAttributeID` для `DimensionAttribute`.|  
  
 Перечисление, соответствующее допустимым значениям элемента `OrderBy` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.OrderBy>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
