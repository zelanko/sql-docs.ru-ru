---
title: Элемент OnlineMode (ASSL) | Документы Microsoft
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
- OnlineMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- OnlineMode
helpviewer_keywords:
- OnlineMode element
ms.assetid: 0bbac4e2-002f-4be4-8dd6-ccd7034f5f93
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3efda242b0563f4b6b853d3bf87b831da1ea8e00
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194124"
---
# <a name="onlinemode-element-assl"></a>Элемент OnlineMode (ASSL)
  Определяет, возвращается ли база данных в состояние «в сети» сразу в начале перестройки кэша или только после окончания перестройки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <OnlineMode>...</OnlineMode>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Немедленно*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Немедленно*|База данных переводится в режим в сети сразу после инициации перестроения кэша.|  
|*OnCacheComplete*|База данных переводится в режим в сети только после завершения перестроения кэша.|  
  
 Перечисление, соответствующее допустимым значениям элемента `OnlineMode` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>См. также  
 [Элемент ProactiveCaching &#40;ASSL&#41;](../objects/proactivecaching-element-assl.md)  
  
  