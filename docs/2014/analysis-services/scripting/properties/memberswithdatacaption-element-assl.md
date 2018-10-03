---
title: Элемент MembersWithDataCaption (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MembersWithDataCaption Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MembersWithDataCaption
helpviewer_keywords:
- MembersWithDataCaption element
ms.assetid: a5d59efd-5d67-485b-a360-67d54a1fe394
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 847a355f2517a5a630096e2617a27bdae396e565
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103904"
---
# <a name="memberswithdatacaption-element-assl"></a>Элемент MembersWithDataCaption (ASSL)
  Задает шаблонную строку, применяемую при создании заголовков для сформированных системой элементов данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributeTranslation> <!-- or DimensionAttribute -->  
   ...  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
   ...  
</AttributeTranslation>  
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
|Родительские элементы|[AttributeTranslation](../data-type/translation-data-type-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение `MembersWithDataCaption` элемент используется только родительскими атрибутами (другими словами, значение [использования](usage-element-dimensionattribute-assl.md) элемент `DimensionAttribute` родительского элемента имеет значение *родительского*) для определения заголовка элементов данных в родительском атрибуте. Дополнительные сведения об элементах данных см. в разделе [Атрибуты в иерархиях типа "родители-потомки"](../../multidimensional-models/parent-child-dimension-attributes.md).  
  
 Элементы, соответствующие родителям элемента `MembersWithDataCaption` в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.AttributeTranslation> и <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Элемент MembersWithData &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [Тип данных AttributeTranslation &#40;ASSL&#41;](../data-type/translation-data-type-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
