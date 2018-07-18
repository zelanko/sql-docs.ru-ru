---
title: Элемент AggregationDesign (ASSL) | Документация Майкрософт
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
- AggregationDesign Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesign
helpviewer_keywords:
- AggregationDesign element
ms.assetid: 80ad98d8-73a8-4353-b5ad-d2a9ac3bc531
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cfebce28ae08d0d76fa851b9d9df3ded8f6c28fc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200094"
---
# <a name="aggregationdesign-element-assl"></a>Элемент AggregationDesign (ASSL)
  Определяет набор определений агрегатов, которые можно совместно использовать в разных секциях в базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationDesigns>  
   <AggregationDesign>  
      <ID>...</ID>  
      <Name>...</Name>  
            <Description>...</Description>  
      <EstimatedRows>...</EstimatedRows>  
      <Dimensions>...</Dimensions>  
            <Aggregations>...</Aggregation>  
      <EstimatedPerformanceGain>...</EstimatedPerformanceGain>  
      <Annotations>...</Annotations>  
   </AggregationDesign>  
</AggregationDesigns>  
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
|Родительские элементы|[AggregationDesigns](../collections/aggregationdesigns-element-assl.md)|  
|Дочерние элементы|[Агрегаты](../collections/aggregations-element-assl.md), [заметки](../collections/annotations-element-assl.md), [описание](../properties/description-element-assl.md), [измерения](../collections/dimensions-element-assl.md), [EstimatedPerformanceGain](../properties/estimatedperformancegain-element-assl.md), [EstimatedRows](../properties/estimatedrows-element-assl.md), [идентификатор](../properties/id-element-assl.md), [имя](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.AggregationDesign>.  
  
## <a name="see-also"></a>См. также  
 [Секции элемент &#40;ASSL&#41;](partition-element-assl.md)   
 [Элемент Aggregation &#40;ASSL&#41;](aggregation-element-assl.md)   
 [Элемент aggregations &#40;ASSL&#41;](../collections/aggregations-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
