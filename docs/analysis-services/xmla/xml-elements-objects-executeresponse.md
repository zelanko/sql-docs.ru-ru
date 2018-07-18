---
title: Элемент ExecuteResponse (XML для Аналитики) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a1ff44c8e2fb23e40aac30e70c73b4d260145bfd
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979126"
---
# <a name="xml-elements---objects---executeresponse"></a>XML элементы — объекты — ExecuteResponse
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит данные, возвращаемые экземпляром служб Analysis Services в ответ на [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) вызова метода.  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ExecuteResponse>  
   <return>  
</ExecuteResponse>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[вернуть](../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 **ExecuteResponse** элемент является элементом верхнего уровня в тексте ответа SOAP для **Execute** метод.  
  
## <a name="see-also"></a>См. также
 [Элемент DiscoverResponse &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)   
 [Объекты &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-objects.md)  
  
  
