---
title: "Элемент RelationshipEndTranslation (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 04e09370-fdfe-4051-9998-4a6859ce8c54
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 715a85f08aef4c4027cf544b9b58da10eb87f850
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="relationshipendtranslation-element-assl"></a>Элемент RelationshipEndTranslation (язык ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет тип-примитив, представляющий локализованный перевод для [RelationshipEnd](../../../analysis-services/scripting/data-type/relationshipend-data-type-assl.md) элемента.  
  
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
|Производные типы данных|[AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Преобразования](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|Дочерние элементы|[Заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [Подпись](../../../analysis-services/scripting/properties/caption-element-assl.md), [CollectionCaption](../../../analysis-services/scripting/properties/caption-element-assl.md), [Описание](../../../analysis-services/scripting/properties/description-element-assl.md), [DisplayFolder](../../../analysis-services/scripting/properties/displayfolder-element-assl.md), [Язык](../../../analysis-services/scripting/properties/language-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
