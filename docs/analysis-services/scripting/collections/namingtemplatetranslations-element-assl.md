---
title: Элемент NamingTemplateTranslations (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- NamingTemplateTranslations Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NamingTemplateTranslations
helpviewer_keywords:
- NamingTemplateTranslations element
ms.assetid: fde65778-1fa3-490a-9874-8bf2052ef25c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8634bb1a8c5ca5acd73a5efa080a30f71139910c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="namingtemplatetranslations-element-assl"></a>Элемент NamingTemplateTranslations (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Предоставляет коллекцию локализованных переводов для элемента [NamingTemplate](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md) , являющегося дочерним для элемента [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md).  
  
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Attribute](../../../analysis-services/scripting/objects/attribute-element-assl.md) типа [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|[NamingTemplateTranslation](../../../analysis-services/scripting/objects/namingtemplatetranslation-element-assl.md) с типом данных [Translation](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Значение элемента **NamingTemplateTranslation** используется только родительскими атрибутами (другими словами, значение элемента [Usage](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) родителя **DimensionAttribute** равно *Parent*).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
