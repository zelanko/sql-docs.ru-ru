---
title: "Элемент DiscoverResponse (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DiscoverResponse Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DiscoverResponse
- microsoft.xml.analysis.discoverresponse
- urn:schemas-microsoft-com:xml-analysis#DiscoverResponse
helpviewer_keywords:
- DiscoverResponse element
ms.assetid: 20e10a82-dbd1-4ead-b92d-f84b4b2f10c6
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8d2483f4a610d1234277f5c686e71eb37266d124
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="xml-elements---objects---discoverresponse"></a>DiscoverResponse элементов - объектов - XML
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
  
## <a name="remarks"></a>Замечания  
 **DiscoverResponse** элемент является элементом верхнего уровня в тексте ответа SOAP для **Discover** метод.  
  
## <a name="see-also"></a>См. также:  
 [Элемент ExecuteResponse &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-objects-executeresponse.md)   
 [Объекты &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-objects.md)  
  
  

