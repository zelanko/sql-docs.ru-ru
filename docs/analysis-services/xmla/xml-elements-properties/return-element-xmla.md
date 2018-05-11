---
title: возвращать Element (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6d6130d367f38a9f2ca04d2ae3ac26c9bcb93c9b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="return-element-xmla"></a>Элемент return (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
|Дочерние элементы|См. таблицу ниже.|  
  
|Предок|Дочерние элементы|  
|--------------|--------------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[корень](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) или [результатов](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 **Возвращают** элемент содержит данные, возвращенные **Discover** и **Execute** методы. Как правило **возвращают** содержит единственный **корневой** элемент, который содержит данные, возвращенные успешной **Discover** или **Execute** вызов метода или XML для аналитики (XMLA) исключения, возвращенные в результате неудачного вызова метода. Если **Execute** содержит метод **пакета** команды, выполняющей несколько операций **возвращают** элемент содержит **результатов** элемент, который в свою очередь, содержит один **корневой** элемент для каждой команды, выполненной успешно или неудачно по **пакета** команды.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
