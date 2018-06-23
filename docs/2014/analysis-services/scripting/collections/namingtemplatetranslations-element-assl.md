---
title: Элемент NamingTemplateTranslations (ASSL) | Документы Microsoft
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
- NamingTemplateTranslations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplateTranslations
helpviewer_keywords:
- NamingTemplateTranslations element
ms.assetid: fde65778-1fa3-490a-9874-8bf2052ef25c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0e22eaea2ab6d19bf1da5620321f0d2002ed382d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096530"
---
# <a name="namingtemplatetranslations-element-assl"></a>Элемент NamingTemplateTranslations (ASSL)
  Предоставляет коллекцию локализованных переводов для элемента [NamingTemplate](../properties/namingtemplate-element-assl.md) , являющегося дочерним для элемента [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Attribute xsi:type="DimensionAttribute">  
   ...  
   <NamingTemplateTranslations>  
            <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
...</NamingTemplateTranslations>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Attribute](../objects/attribute-element-assl.md) типа [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|[NamingTemplateTranslation](../objects/translation-element-assl.md) с типом данных [Translation](translations-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Значение `NamingTemplateTranslation` элемент используется только родительскими атрибутами (другими словами, значение [использование](../properties/usage-element-dimensionattribute-assl.md) родителя `DimensionAttribute` равно *родительского*.)  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  