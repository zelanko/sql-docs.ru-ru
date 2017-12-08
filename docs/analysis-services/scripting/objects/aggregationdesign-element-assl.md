---
title: "Элемент AggregationDesign (ASSL) | Документы Microsoft"
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
apiname: AggregationDesign Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AggregationDesign
helpviewer_keywords: AggregationDesign element
ms.assetid: 80ad98d8-73a8-4353-b5ad-d2a9ac3bc531
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 81d1fbd4f314b713e0177af58ef27b3caed4f28a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
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
|Количество элементов|0–n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AggregationDesigns](../../../analysis-services/scripting/collections/aggregationdesigns-element-assl.md)|  
|Дочерние элементы|[Агрегаты](../../../analysis-services/scripting/collections/aggregations-element-assl.md), [заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [описание](../../../analysis-services/scripting/properties/description-element-assl.md), [измерения](../../../analysis-services/scripting/collections/dimensions-element-assl.md), [EstimatedPerformanceGain](../../../analysis-services/scripting/properties/estimatedperformancegain-element-assl.md), [EstimatedRows](../../../analysis-services/scripting/properties/estimatedrows-element-assl.md), [идентификатор](../../../analysis-services/scripting/properties/id-element-assl.md), [имя](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AggregationDesign>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент partition &#40; ASSL &#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)   
 [Элемент Aggregation &#40; ASSL &#41;](../../../analysis-services/scripting/objects/aggregation-element-assl.md)   
 [Элемент aggregations &#40; ASSL &#41;](../../../analysis-services/scripting/collections/aggregations-element-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
