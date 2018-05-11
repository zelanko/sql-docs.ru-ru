---
title: Элемент DiscoverResponse (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b2a581b447831dfb25d345923d4e0e1cbdaf517b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---objects---discoverresponse"></a>DiscoverResponse элементов - объектов - XML
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит информацию, возвращаемую экземпляром служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в ответ на [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) вызова метода.  
  
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
  
  
