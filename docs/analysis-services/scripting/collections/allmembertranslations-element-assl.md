---
title: "Элемент AllMemberTranslations (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
apiname: AllMemberTranslations Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AllMemberTranslations
helpviewer_keywords: AllMemberTranslations element
ms.assetid: 982ee2bf-c88d-4da5-a679-7a6b08a48a0d
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 63eb22e9012da8043a57956bada680f0c30dfbf7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="allmembertranslations-element-assl"></a>Элемент AllMemberTranslations (ASSL)
  Содержит коллекцию элементов [перевода](../../../analysis-services/scripting/objects/translation-element-assl.md) для заголовка элемента «все» [иерархии](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Hierarchy>  
   ...  
   <AllMemberTranslations>  
      <AllMemberTranslation xsi:type="Translation">...  
            </AllMemberTranslation>  
   </AllMemberTranslations>  
      ...  
</Hierarchy>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|нет (коллекция)|  
|Значение по умолчанию|нет (коллекция)|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Hierarchy](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)|  
|Дочерние элементы|[AllMemberTranslation](../../../analysis-services/scripting/objects/allmembertranslation-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родительский **AllMemberTranslations** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Translation &#40; ASSL &#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)   
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
