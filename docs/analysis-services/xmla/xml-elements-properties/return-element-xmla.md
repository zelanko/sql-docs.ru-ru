---
title: "возвращать Element (XMLA) | Документы Microsoft"
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
- return Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.return
- http://schemas.microsoft.com/analysisservices/2003/engine#return
- urn:schemas-microsoft-com:xml-analysis#return
helpviewer_keywords:
- return element
ms.assetid: 3cfe8b74-fec3-4987-a74a-5f731444e024
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 06b93a7d4c785f8e298a40d6b0accd2ad945b53e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="return-element-xmla"></a>Элемент return (XML для аналитики)
  Содержит данные, возвращенные [DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md) в ответ на [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) вызова метода или [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md) в ответ на [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) вызова метода.  
  
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
|Родительские элементы|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md), [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|  
|Дочерние элементы|См. в следующей таблице.|  
  
|Предок|Дочерние элементы|  
|--------------|--------------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[корень](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) или [результатов](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 **Возвращают** элемент содержит данные, возвращенные **Discover** и **Execute** методы. Как правило **возвращают** содержит единственный **корневой** элемент, который содержит данные, возвращенные успешной **Discover** или **Execute** вызов метода или XML для аналитики (XMLA) исключения, возвращенные в результате неудачного вызова метода. Если **Execute** содержит метод **пакета** команды, выполняющей несколько операций **возвращают** элемент содержит **результатов** элемент, который в свою очередь, содержит один **корневой** элемент для каждой команды, выполненной успешно или неудачно по **пакета** команды.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
