---
title: "Элемент aggregations (ASSL) | Документы Microsoft"
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
apiname: Aggregations Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Aggregations
helpviewer_keywords: Aggregations element
ms.assetid: 79b7de7a-53b2-4202-bc0f-de1daaf1b179
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a5bedb657cb1f0f1ef57545df2b9c559e3d1f713
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="aggregations-element-assl"></a>Элемент Aggregations (ASSL)
  Содержит коллекцию агрегатов, определенных для [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationDesign>  
   ...  
   <Aggregations>  
      <Aggregation>...</Aggregation>  
   </Aggregations>  
   ...  
</AggregationDimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|нет (коллекция)|  
|Значение по умолчанию|нет (коллекция)|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)|  
|Дочерние элементы|[Агрегат](../../../analysis-services/scripting/objects/aggregation-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AggregationCollection>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент MeasureGroup &#40; ASSL &#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)   
 [Элемент partition &#40; ASSL &#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)   
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
