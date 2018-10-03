---
title: Запрашивает элемент (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Queries Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.queries
- urn:schemas-microsoft-com:xml-analysis#Queries
- http://schemas.microsoft.com/analysisservices/2003/engine#Queries
helpviewer_keywords:
- Queries element
ms.assetid: e199412a-23f1-4d11-9e72-11f184ad9602
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7fbec1d4ef3c5da759c60039196dc16735da803e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48225804"
---
# <a name="queries-element-xmla"></a>Элемент Queries (XML для аналитики)
  Содержит коллекцию элементов [Query](query-element-xmla.md) , использующихся командой [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md) во время оптимизации с учетом использования.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DesignAggregations>  
   ...  
   <Queries>  
      <Query>...</Query>  
   </Queries>  
   ...  
</DesignAggregations>  
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
|Родительские элементы|[DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md)|  
|Дочерние элементы|[Запрос](query-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
