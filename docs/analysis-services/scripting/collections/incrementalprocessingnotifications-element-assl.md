---
title: "Элемент IncrementalProcessingNotifications (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IncrementalProcessingNotifications Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: IncrementalProcessingNotifications element
ms.assetid: 46f3c9d0-46cc-4833-8f15-7831207f57ce
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4d8603e76e26b9197cbbc17021bb0a254de96abc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="incrementalprocessingnotifications-element-assl"></a>Элемент IncrementalProcessingNotifications (ASSL)
  Содержит коллекцию элементов [IncrementalProcessingNotification](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md) элементы, которые содержат сведения о [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) о запросах, необходимо выполнить, чтобы определить ход выполнения добавочной обработки.  
  
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
|Родительские элементы|[ProactiveCachingIncrementalProcessingBinding](../../../analysis-services/scripting/data-type/proactivecachingincrementalprocessingbinding-data-type-assl.md)|  
|Дочерние элементы|[IncrementalProcessingNotification](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.IncrementalProcessingNotificationCollection>.  
  
## <a name="see-also"></a>См. также:  
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
