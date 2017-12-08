---
title: "Тип данных AttributeTranslation (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AttributeTranslation Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AttributeTranslation
helpviewer_keywords: AttributeTranslation data type
ms.assetid: a0e29941-ef08-42ad-ab9c-b2efd7910895
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b28b436df1b4c8dc37be83fb29c36be4d1c8ad0e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="attributetranslation-data-type-assl"></a>Тип данных AttributeTranslation (ASSL)
  Определяет производный тип данных, представляющий перевод, связанный с [атрибут](../../../analysis-services/scripting/objects/attribute-element-assl.md) элемента  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributeTranslation>  
   <!-- The following elements extend Translation -->  
   <CaptionColumn>...</CaptionColumn>  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
</AttributeTranslation>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Перевод](../../../analysis-services/scripting/data-type/translation-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[CaptionColumn](../../../analysis-services/scripting/objects/captioncolumn-element-assl.md), [MembersWithDataCaption](../../../analysis-services/scripting/properties/memberswithdatacaption-element-assl.md)|  
|Производные элементы|В разделе [перевода](../../../analysis-services/scripting/objects/translation-element-assl.md) ([переводы](../../../analysis-services/scripting/collections/translations-element-assl.md) коллекцию [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md) или [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AttributeTranslation>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
