---
title: возвращать Element (XMLA) | Документы Microsoft
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
- return Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.return
- http://schemas.microsoft.com/analysisservices/2003/engine#return
- urn:schemas-microsoft-com:xml-analysis#return
helpviewer_keywords:
- return element
ms.assetid: 3cfe8b74-fec3-4987-a74a-5f731444e024
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 1a4468ce3d4b14ff9cd9db7c9373083aad75d3eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086728"
---
# <a name="return-element-xmla"></a>Элемент return (XML для аналитики)
  Содержит данные, возвращенные [DiscoverResponse](../xml-elements-objects-discoverresponse.md) в ответ на [Discover](../xml-elements-methods-discover.md) вызова метода или [ExecuteResponse](../xml-elements-objects-executeresponse.md) в ответ на [Execute](../xml-elements-methods-execute.md) вызова метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DiscoverResponse> <!-- or ExecuteResponse -->  
   <return>  
      <root>...</root>  
      <!-- or -->  
      <results>...</results> <!-- ExecuteResponse only -->  
   </return>  
</DiscoverResponse>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DiscoverResponse](../xml-elements-objects-discoverresponse.md), [ExecuteResponse](../xml-elements-objects-executeresponse.md)|  
|Предок:[DiscoverResponse](../xml-elements-objects-discoverresponse.md)|Дочерние: <br />                        [корень](root-element-xmla.md)|  
|Предка: <br />                        [ExecuteResponse](../xml-elements-objects-executeresponse.md)|Дочерние: [корневой](root-element-xmla.md) или [результатов](results-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент `return` содержит данные, возвращенные методами `Discover` и `Execute`. Как правило, элемент `return` содержит единственный элемент `root`, который включает данные, возвращенные в результате успешного вызова метода `Discover` или `Execute`, или исключение XMLA, возвращенное в результате неудачного вызова метода. Если метод `Execute` содержит команду `Batch`, которая выполняет несколько операций, то элемент `return` содержит элемент `results`, который, в свою очередь, включает по одному элементу `root` для каждой команды, выполненной командой `Batch` успешно или неудачно.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  