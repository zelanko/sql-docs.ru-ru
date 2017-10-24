---
title: "Элемент UnknownMemberTranslations (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- UnknownMemberTranslations Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- UnknownMemberTranslations
helpviewer_keywords:
- UnknownMemberTranslations element
ms.assetid: 72920843-2d43-4ff4-b38e-19c9a7451cb2
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: be3d45b88c99d7bce92e332154c09461905b1228
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="unknownmembertranslations-element-assl"></a>Элемент UnknownMemberTranslations (ASSL)
  Содержит коллекцию переводов для заголовка элемента [UnknownMember](../../../analysis-services/scripting/properties/unknownmember-element-assl.md) элемента измерения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension>  
   ...  
   <UnknownMemberTranslations>  
      <UnknownMemberTranslation xsi:type="Translation ">...</UnknownMemberTranslation>  
      </UnknownMemberTranslations>  
   ...  
</Dimension>  
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
|Родительские элементы|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Дочерние элементы|[UnknownMemberTranslation](../../../analysis-services/scripting/objects/unknownmembertranslation-element-assl.md) типа [перевода](../../../analysis-services/scripting/data-type/translation-data-type-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **UnknownMemberTranslations** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>См. также:  
 [Тип данных Translation &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/translation-data-type-assl.md)   
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

