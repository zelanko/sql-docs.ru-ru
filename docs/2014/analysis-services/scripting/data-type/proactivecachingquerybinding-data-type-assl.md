---
title: Тип данных ProactiveCachingQueryBinding (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ProactiveCachingQueryBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingQueryBinding data type
ms.assetid: c1b06e50-9e68-40db-bdab-fc2cb3a8ff64
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d7b9c4aea38bb66277467275d2cf89a04cc3144a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087634"
---
# <a name="proactivecachingquerybinding-data-type-assl"></a>Тип данных ProactiveCachingQueryBinding (ASSL)
  Определяет производный тип данных, представляющий сведения для [ProactiveCaching](../objects/proactivecaching-element-assl.md) об изменениях источника данных в таблицах и представлениях, определяемых через исполнение указанных запросов, которые требуют перестройки кэша.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCachingQueryBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <RefreshInterval>...</RefreshInterval>  
   <QueryNotification>...</QueryNotification>  
</ProactiveCachingQueryBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[ProactiveCachingBinding](binding-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[QueryNotification](../objects/querynotification-element-assl.md), [RefreshInterval](../properties/refreshinterval-element-assl.md)|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о `ProactiveCachingBinding` типа, включая таблицу иерархии наследования `ProactiveCachingBinding` типов, см. в разделе [тип данных ProactiveCachingBinding &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Дополнительные сведения о `Binding` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) типа `Binding` тип и иерархию наследования `Binding` типов, см. в разделе [типа привязки данных &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Обзор привязки данных в языке ASSL, см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.ProactiveCachingQueryBinding>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
