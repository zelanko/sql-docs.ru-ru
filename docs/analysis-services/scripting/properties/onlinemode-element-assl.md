---
title: Элемент OnlineMode (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e02252c66333e6d75bb72871105604f35cd688c5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="onlinemode-element-assl"></a>Элемент OnlineMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Немедленно*|База данных переводится в режим в сети сразу после инициации перестроения кэша.|  
|*OnCacheComplete*|База данных переводится в режим в сети только после завершения перестроения кэша.|  
  
 Перечисление, соответствующее разрешенным значениям для **OnlineMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>См. также  
 [Элемент ProactiveCaching &#40;ASSL&#41;](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)  
  
  
