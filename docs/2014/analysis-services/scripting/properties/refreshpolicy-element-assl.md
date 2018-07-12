---
title: Элемент RefreshPolicy (ASSL) | Документация Майкрософт
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
- RefreshPolicy Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RefreshPolicy
helpviewer_keywords:
- RefreshPolicy element
ms.assetid: f4c36280-1a39-4f1c-a3ab-fbeb81742d6d
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cf0aa9478a44e7479b20357ae56317b90801f77f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277620"
---
# <a name="refreshpolicy-element-assl"></a>Элемент RefreshPolicy (ASSL)
  Определяет, как часто динамической части измерения или группы мер (как указано [сохраняемости](persistence-element-assl.md) элемент) проверки на наличие изменений.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <RefreshPolicy>...</RefreshPolicy>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
|Предок или родитель|Значение по умолчанию|  
|------------------------|-------------------|  
|[DimensionBinding](../data-type/binding-data-type-assl.md)|*ByQuery*|  
|[MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|None|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DimensionBinding](../data-type/binding-data-type-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*ByQuery*|Каждый запрос проверяет, не изменился ли источник данных.|  
|*ByInterval*|Источник данных проверяется только наличие изменений в интервале, заданном элементом [RefreshInterval](refreshinterval-element-assl.md).|  
  
 Перечисление, соответствующее допустимым значениям элемента `RefreshPolicy` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.RefreshPolicy>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Persistence &#40;ASSL&#41;](persistence-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
