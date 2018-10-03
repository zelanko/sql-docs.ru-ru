---
title: Элемент SilenceOverrideInterval (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- SilenceOverrideInterval Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SilenceOverrideInterval
helpviewer_keywords:
- SilenceOverrideInterval element
ms.assetid: 0dcd2db4-9bc0-4460-b1dd-def0b38c4617
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5b52e5a7caa3f6bd72d4bf598392a03cf744cbd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120418"
---
# <a name="silenceoverrideinterval-element-assl"></a>Элемент SilenceOverrideInterval (ASSL)
  Определяет количество времени, которое должно пройти после получения первичного уведомления до того, как начнется безусловное создание образа многомерного OLAP (MOLAP).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <SilenceOverrideInterval>...</SilenceOverrideInterval>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|duration|  
|Значение по умолчанию|P0s|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если уведомление получено во время интервала бездействия, то значение `SilenceOverrideInterval` заменяет значение `SilenceInterval`.  
  
 Элемент, соответствующий родителю параметра `SilenceOverrideInterval` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
