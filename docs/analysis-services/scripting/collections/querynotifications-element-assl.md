---
title: "Элемент QueryNotifications (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- QueryNotifications Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- QueryNotifications element
ms.assetid: 0e7e951f-c8b9-4492-bb01-e4b5d16edde6
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 73b252a1c3d31c180f9a6b876ab768fa74499421
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="querynotifications-element-assl"></a>Элемент QueryNotifications (ASSL)
  Содержит коллекцию элементов [QueryNotification](../../../analysis-services/scripting/objects/querynotification-element-assl.md) элементы, которые содержат сведения о [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) о запросах, необходимо выполнить, чтобы определить, был ли изменен источник данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCachingQueryBinding>  
   ...  
   <QueryNotifications>  
      <QueryNotification>...</QueryNotification>  
...</QueryNotifications>  
   ...  
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
|Родительские элементы|[ProactiveCachingQueryBinding](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)|  
|Дочерние элементы|[QueryNotification](../../../analysis-services/scripting/objects/querynotification-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.QueryNotificationCollection>.  
  
## <a name="see-also"></a>См. также:  
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
