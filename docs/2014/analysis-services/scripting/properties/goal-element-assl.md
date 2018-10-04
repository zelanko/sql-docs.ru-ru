---
title: Элемент Goal (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Goal Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Goal
helpviewer_keywords:
- Goal element
ms.assetid: 75fa5b57-418e-43ad-8704-764e4f0a40cf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fe7ff6a2623db0c0f6b1cb5a3d1c09010a984e72
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117604"
---
# <a name="goal-element-assl"></a>Элемент Goal (ASSL)
  Определяет целевое в [ключевого показателя эффективности](../objects/kpi-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Kpi>  
   ...  
   <Goal>...</Goal>  
   ...  
</Kpi>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Ключевой показатель эффективности](../objects/kpi-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `Goal` содержит многомерное выражение.  
  
 Элемент, соответствующий родителю параметра `Goal` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Status &#40;ASSL&#41;](status-element-assl.md)   
 [Элемент Trend &#40;ASSL&#41;](trend-element-assl.md)   
 [Значение элемента &#40;ASSL&#41;](value-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
