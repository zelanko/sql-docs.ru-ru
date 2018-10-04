---
title: Элемент IncrementalProcessingNotifications (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- IncrementalProcessingNotifications Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- IncrementalProcessingNotifications element
ms.assetid: 46f3c9d0-46cc-4833-8f15-7831207f57ce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8feef546f55b2a018144f8b0d9db27d03a2e3638
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200644"
---
# <a name="incrementalprocessingnotifications-element-assl"></a>Элемент IncrementalProcessingNotifications (ASSL)
  Содержит коллекцию элементов [IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md) элементы, которые содержат сведения, которые [ProactiveCaching](../objects/proactivecaching-element-assl.md) элемент о запросах, необходимо выполнить, чтобы узнать ход выполнения добавочной обработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCachingIncrementalProcessingBinding>  
   <IncrementalProcessingNotifications>  
      <IncrementalProcessingNotification>...  
   ...</IncrementalProcessingNotification>  
   </IncrementalProcessingNotifications>  
</ProactiveCachingQueryBinding>  
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
|Родительские элементы|[ProactiveCachingIncrementalProcessingBinding](../data-type/binding-data-type-assl.md)|  
|Дочерние элементы|[IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.IncrementalProcessingNotificationCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
