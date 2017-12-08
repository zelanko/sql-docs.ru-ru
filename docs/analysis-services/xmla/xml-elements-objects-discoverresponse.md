---
title: "Элемент DiscoverResponse (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DiscoverResponse Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DiscoverResponse
- microsoft.xml.analysis.discoverresponse
- urn:schemas-microsoft-com:xml-analysis#DiscoverResponse
helpviewer_keywords: DiscoverResponse element
ms.assetid: 20e10a82-dbd1-4ead-b92d-f84b4b2f10c6
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6f5051e1c5a9841ccf4a949a6c5b99f45a9fc8d2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
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
  
  
