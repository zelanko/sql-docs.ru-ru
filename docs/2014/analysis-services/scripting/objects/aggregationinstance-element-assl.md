---
title: Элемент AggregationInstance (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AggregationInstance Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationInstance element
ms.assetid: 2e77e9e1-9f2c-4df4-9aa6-5b7b911016a3
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fe8d4f62355888b9d145979af75ea312e32d554c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193460"
---
# <a name="aggregationinstance-element-assl"></a>Элемент AggregationInstance (ASSL)
  Определяет экземпляр агрегата для секции.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationInstances>  
   <AggregationInstance>  
      <AggregationType>...</AggregationType>  
      <AggregationID>...</AggregationID>  
      <Source>...</Source>  
      <Dimensions>...</Dimensions>  
      <Measures>...</Measures>  
      <Annotations>...</Annotations>  
   </AggregationInstance>  
</AggregationInstances>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AggregationInstances](../collections/aggregationinstances-element-assl.md)|  
|Дочерние элементы|[AggregationID](../properties/id-element-assl.md), [AggregationType](../properties/aggregationtype-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [Dimensions](../collections/dimensions-element-assl.md), [Measures](../collections/measures-element-assl.md), [Source](../properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 При [секции](partition-element-assl.md) элемент использует [AggregationDesign](aggregationdesign-element-assl.md) для создания агрегатов для этой секции, каждой [статистической обработки](aggregation-element-assl.md) в `AggregationDesign` — экземпляр для этой секции. В одной и той же статистической схеме может использоваться несколько секций для создания нескольких экземпляров определенного агрегата. Элемент `AggregationInstance` представляет экземпляр определенного статистического вычисления.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>См. также  
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  