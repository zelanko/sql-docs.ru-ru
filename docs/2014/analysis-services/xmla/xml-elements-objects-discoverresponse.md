---
title: Элемент DiscoverResponse (XML для Аналитики) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DiscoverResponse Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DiscoverResponse
- microsoft.xml.analysis.discoverresponse
- urn:schemas-microsoft-com:xml-analysis#DiscoverResponse
helpviewer_keywords:
- DiscoverResponse element
ms.assetid: 20e10a82-dbd1-4ead-b92d-f84b4b2f10c6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 763724fb08a849000cb960435847a84447ba5674
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105394"
---
# <a name="discoverresponse-element-xmla"></a>Элемент DiscoverResponse (XML для аналитики)
  Содержит данные, возвращаемые экземпляром служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в ответ на [Discover](xml-elements-methods-discover.md) вызова метода.  
  
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
|Дочерние элементы|[вернуть](xml-elements-properties/return-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент `DiscoverResponse` является элементом верхнего уровня в тексте ответа SOAP для метода `Discover`.  
  
## <a name="see-also"></a>См. также  
 [Элемент ExecuteResponse &#40;XML для Аналитики&#41;](xml-elements-objects-executeresponse.md)   
 [Объекты &#40;XML для Аналитики&#41;](xml-elements-objects.md)  
  
  
