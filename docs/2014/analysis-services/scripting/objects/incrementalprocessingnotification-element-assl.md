---
title: Элемент IncrementalProcessingNotification (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- IncrementalProcessingNotification Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- IncrementalProcessingNotification element
ms.assetid: bfc9b0a4-4043-4aaf-82d9-67e7f1d1eb81
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 639d58928b27e965a707602c0ea124c9078e5b47
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120744"
---
# <a name="incrementalprocessingnotification-element-assl"></a>Элемент IncrementalProcessingNotification (ASSL)
  Содержит сведения о [ProactiveCaching](proactivecaching-element-assl.md) о запросе, необходимо выполнить, чтобы узнать ход выполнения добавочной обработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<IncrementalProcessingNotifications>  
   <IncrementalProcessingNotification xsi:type="IncrementalProcessingNotification">...</IncrementalProcessingNotification>  
</IncrementalProcessingNotifications>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[IncrementalProcessingNotification](../data-type/incrementalprocessingnotification-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|1-N: обязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[IncrementalProcessingNotifications](../collections/incrementalprocessingnotifications-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных ProactiveCachingQueryBinding &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [Элемент ProactiveCaching &#40;ASSL&#41;](proactivecaching-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
