---
title: Элемент TableNotifications (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- TableNotifications Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- TableNotifications element
ms.assetid: 4cecdfea-0d4d-4bd6-bbb3-4d0d2284c665
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 87a1328bf4e7e302b16fa4d0a45fc105ce820d54
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101835"
---
# <a name="tablenotifications-element-assl"></a>Элемент TableNotifications (ASSL)
  Содержит коллекцию элементов [TableNotification](../objects/tablenotification-element-assl.md) элементы, которые предоставляют сведения для [ProactiveCaching](../objects/proactivecaching-element-assl.md) о таблиц или представлений в источнике данных, которые были изменены.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCachingTablesBinding>  
   <TableNotifications>  
      <TableNotification>...</TableNotification>  
...</TableNotifications>  
</ProactiveCachingTablesBinding>  
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
|Родительские элементы|[ProactiveCachingTablesBinding](../data-type/binding-data-type-assl.md)|  
|Дочерние элементы|[TableNotification](../objects/tablenotification-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.TableNotificationCollection>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных ProactiveCachingBinding &#40;ASSL&#41;](../data-type/proactivecachingbinding-data-type-assl.md)   
 [Тип данных ProactiveCachingObjectNotificationBinding &#40;ASSL&#41;](../data-type/proactivecachingobjectnotificationbinding-data-type-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  