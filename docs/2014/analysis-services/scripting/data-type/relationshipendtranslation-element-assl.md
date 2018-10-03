---
title: Элемент RelationshipEndTranslation (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 04e09370-fdfe-4051-9998-4a6859ce8c54
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0e36c3f114f70c17022e4fe0c11494f5e9c38748
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131524"
---
# <a name="relationshipendtranslation-element-assl"></a>Элемент RelationshipEndTranslation (язык ASSL)
  Определяет примитивный тип данных, представляющий локализованный перевод для элемента [RelationshipEnd](relationshipend-data-type-assl.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<RelationshipEndTranslation>  
   <Language>...</Language>  
   <Caption>...</Caption>  
   <CollectionCaption>...</Caption>  
   <Description>...</Description>  
   <DisplayFolder>...</DisplayFolder>  
   <Annotations>...</Annotations>  
</RelationshipEndTranslation>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|[AttributeTranslation](translation-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Преобразования](../collections/translations-element-assl.md)|  
|Дочерние элементы|[Заметки](../collections/annotations-element-assl.md), [Подпись](../properties/caption-element-assl.md), [CollectionCaption](../properties/caption-element-assl.md), [Описание](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [Язык](../properties/language-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
