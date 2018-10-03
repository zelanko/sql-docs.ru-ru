---
title: Элемент ExecuteResponse (XML для Аналитики) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ExecuteResponse Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ExecuteResponse
- http://schemas.microsoft.com/analysisservices/2003/engine#ExecuteResponse
- microsoft.xml.analysis.executeresponse
helpviewer_keywords:
- ExecuteResponse element
ms.assetid: 6edb1b82-da4c-4cd9-9385-bea04032f0eb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 002da257a4d1137b0e52743eec99f1b0aced56c0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48047585"
---
# <a name="executeresponse-element-xmla"></a>Элемент ExecuteResponse (XML для аналитики)
  Содержит данные, возвращаемые экземпляром служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в ответ на [Execute](xml-elements-methods-execute.md) вызова метода.  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ExecuteResponse>  
   <return>  
</ExecuteResponse>  
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
 Элемент `ExecuteResponse` является элементом верхнего уровня в тексте ответа SOAP для метода `Execute`.  
  
## <a name="see-also"></a>См. также  
 [Элемент DiscoverResponse &#40;XML для Аналитики&#41;](xml-elements-objects-discoverresponse.md)   
 [Объекты &#40;XML для Аналитики&#41;](xml-elements-objects.md)  
  
  
