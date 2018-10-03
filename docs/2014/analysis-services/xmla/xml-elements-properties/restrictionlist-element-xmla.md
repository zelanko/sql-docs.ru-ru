---
title: Элемент RestrictionList (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cad57213c69c63dbc45e476d0163a46c111bc8a9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067954"
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
  
  
