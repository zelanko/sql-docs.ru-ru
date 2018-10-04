---
title: Элемент aggregations (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Aggregations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Aggregations
helpviewer_keywords:
- Aggregations element
ms.assetid: 79b7de7a-53b2-4202-bc0f-de1daaf1b179
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2d64819bb59cbd86b2179abfbfd3afb5639577a0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177594"
---
# <a name="aggregations-element-assl"></a>Элемент Aggregations (ASSL)
  Содержит коллекцию агрегатов, определенных для [AggregationDesign](../objects/aggregationdesign-element-assl.md) элемент.  
  
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[AggregationDesign](../objects/aggregationdesign-element-assl.md)|  
|Дочерние элементы|[Статистической обработки](../objects/aggregation-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.AggregationCollection>.  
  
## <a name="see-also"></a>См. также  
 [Элемент MeasureGroup &#40;ASSL&#41;](../objects/group-element-assl.md)   
 [Секции элемент &#40;ASSL&#41;](../objects/partition-element-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
