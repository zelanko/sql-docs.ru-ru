---
title: Элемент NamingTemplateTranslation (ASSL) | Документы Microsoft
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
- NamingTemplateTranslation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplateTranslation
helpviewer_keywords:
- NamingTemplateTranslation element
ms.assetid: 4a97a31d-23bc-4afd-a4dc-bc0ad7121f08
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dc6c6689f4028c0983267a38435c76e7258768a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188776"
---
# <a name="namingtemplatetranslation-element-assl"></a>Элемент NamingTemplateTranslation (ASSL)
  Предоставляет локализованный перевод элемента [NamingTemplate](../properties/namingtemplate-element-assl.md) для родительского [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) тип данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<NamingTemplateTranslations>  
   <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
</NamingTemplateTranslations>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[Перевод](translation-element-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[NamingTemplateTranslations](../collections/translations-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение `NamingTemplateTranslation` элемент используется только родительскими атрибутами (другими словами, значение [использование](../properties/usage-element-dimensionattribute-assl.md) элемент `DimensionAttribute` имеет значение родительского *родительского*) для хранения локализации Перевод `NamingTemplate` значение для данного языка.  
  
 Элемент, соответствующий родителю параметра `NamingTemplateTranslations` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Элемент NamingTemplate &#40;ASSL&#41;](../properties/namingtemplate-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  