---
title: Элемент DiscoverResponse (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b9ad13a08b6afa19b59dbdaf8d43686c13649a43
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574352"
---
# <a name="xml-elements---objects---discoverresponse"></a>DiscoverResponse элементов - объектов - XML
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит информацию, возвращаемую экземпляром служб Analysis Services в ответ на [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) вызова метода.  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DiscoverResponse>  
   <return>  
</DiscoverResponse>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Возврат](../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 **DiscoverResponse** элемент является элементом верхнего уровня в тексте ответа SOAP для **Discover** метод.  
  
## <a name="see-also"></a>См. также
 [Элемент ExecuteResponse &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-objects-executeresponse.md)   
 [Объекты &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-objects.md)  
  
  
