---
title: "Элемент AllMemberTranslation (ASSL) | Документы Microsoft"
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
apiname: AllMemberTranslation Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AllMemberTranslation
helpviewer_keywords: AllMemberTranslation element
ms.assetid: 31ec0c44-8f1d-457c-9e8b-61dd5bc468f7
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 51bc23aaadefbcaea4a492203a46c52424536468
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="allmembertranslation-element-assl"></a>Элемент AllMemberTranslation (ASSL)
  Содержит перевод заголовка элемента «все» [иерархии](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AllMemberTranslations>  
   <AllMemberTranslation xsi:type="Translation">...  
   </AllMemberTranslation>  
</AllMemberTranslations>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[Перевод](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[AllMemberTranslations](../../../analysis-services/scripting/collections/allmembertranslations-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **AllMemberTranslations** коллекции в объектной модели Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Translation &#40; ASSL &#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)   
 [Элемент Hierarchy &#40; ASSL &#41;](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
