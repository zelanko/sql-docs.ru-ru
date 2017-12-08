---
title: "Элемент RestrictionList (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: RestrictionList Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#RestrictionList
- microsoft.xml.analysis.restrictionlist
- http://schemas.microsoft.com/analysisservices/2003/engine#RestrictionList
helpviewer_keywords: RestrictionList element
ms.assetid: 2297c005-381e-49a4-a207-826f7f9ea93a
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af4df63d245aacd861c9f4a2a1d8a4c9d8a9b01d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="restrictionlist-element-xmla"></a>Элемент RestrictionList (XML для аналитики)
  Содержит коллекцию столбцов ограничений и значений, используемых методом [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Restrictions>  
   <RestrictionList>  
      <!-- Zero or more restriction columns and values -->  
   </RestrictionList>  
</Restrictions>  
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
|Родительские элементы|[Ограничения](../../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
|Дочерние элементы|Столбцы и значения ограничений (см. примечания).|  
  
## <a name="remarks"></a>Замечания  
 Элемент **RestrictionList** содержит коллекцию столбцов ограничений, которые могут служить в качестве фильтров для данных, возвращаемых методом **Discover** . Каждый столбец ограничений в элементе **RestrictionList** определен с помощью отдельного XML-элемента. Значением столбца ограничений являются данные, содержащиеся в этом XML-элементе, а имя столбца ограничений соответствует имени XML-элемента.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
