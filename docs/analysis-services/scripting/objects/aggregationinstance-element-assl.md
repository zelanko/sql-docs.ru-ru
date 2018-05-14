---
title: Элемент AggregationInstance (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c8f24bbaf0660c690697dad015fa28c412a633a3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="aggregationinstance-element-assl"></a>Элемент AggregationInstance (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Родительские элементы|[AggregationInstances](../../../analysis-services/scripting/collections/aggregationinstances-element-assl.md)|  
|Дочерние элементы|[AggregationID](../../../analysis-services/scripting/properties/aggregationid-element-assl.md), [AggregationType](../../../analysis-services/scripting/properties/aggregationtype-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [Dimensions](../../../analysis-services/scripting/collections/dimensions-element-assl.md), [Measures](../../../analysis-services/scripting/collections/measures-element-assl.md), [Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Если в элементе [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md) используется элемент [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) для создания агрегатов применительно к этой секции, для каждого объекта [Aggregation](../../../analysis-services/scripting/objects/aggregation-element-assl.md) в схеме **AggregationDesign** создается экземпляр для этой секции. В одной и той же статистической схеме может использоваться несколько секций для создания нескольких экземпляров определенного агрегата. Элемент **AggregationInstance** представляет экземпляр определенного статистического вычисления.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>См. также  
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
