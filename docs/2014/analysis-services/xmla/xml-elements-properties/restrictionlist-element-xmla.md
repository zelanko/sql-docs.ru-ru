---
title: Элемент RestrictionList (XMLA) | Документация Майкрософт
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
- RestrictionList Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#RestrictionList
- microsoft.xml.analysis.restrictionlist
- http://schemas.microsoft.com/analysisservices/2003/engine#RestrictionList
helpviewer_keywords:
- RestrictionList element
ms.assetid: 2297c005-381e-49a4-a207-826f7f9ea93a
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 045c5644608c7f9537124450ef2c5637eebbb796
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37314594"
---
# <a name="restrictionlist-element-xmla"></a>Элемент RestrictionList (XML для аналитики)
  Содержит коллекцию столбцов ограничений и значений, используемых методом [Discover](../xml-elements-methods-discover.md) .  
  
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Ограничения](restrictions-element-xmla.md)|  
|Дочерние элементы|Столбцы и значения ограничений (см. примечания).|  
  
## <a name="remarks"></a>Примечания  
 Элемент `RestrictionList` содержит коллекцию столбцов ограничений, которые могут служить в качестве фильтров для данных, возвращаемых методом `Discover`. Каждый столбец ограничений в элементе `RestrictionList` определен с помощью отдельного XML-элемента. Значением столбца ограничений являются данные, содержащиеся в этом XML-элементе, а имя столбца ограничений соответствует имени XML-элемента.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
