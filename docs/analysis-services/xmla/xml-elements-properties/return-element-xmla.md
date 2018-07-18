---
title: Элемент Return (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e8746fb9f8b397ef50b1a5c66a2132e5f0cf5c87
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37968446"
---
# <a name="return-element-xmla"></a>Элемент return (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит данные, возвращенные [DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md) элемента в ответ на [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) вызов метода или [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md) элемента в ответ на [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) вызова метода.  
  
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
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md), [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|  
|Дочерние элементы|См. таблицу ниже.|  
  
|Предок|Дочерние элементы|  
|--------------|--------------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) или [результаты](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 **Возвращают** элемент содержит данные, возвращаемые **Discover** и **Execute** методы. Как правило **возвращают** элемент содержит один **корневой** элемент, содержащий данные, возвращенные успешное выполнение **Discover** или **Execute** вызов метода или XML для аналитики (XMLA) исключения, возвращаемые неудачного вызова метода. Если **Execute** содержит метод **пакета** команды, выполняющей несколько операций **возвращают** элемент содержит **результатов** элемент, который, в свою очередь, содержит один **корневой** -элемент для каждой команды, выполненной успешно или неудачно по **пакета** команды.  
  
## <a name="see-also"></a>См. также
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
