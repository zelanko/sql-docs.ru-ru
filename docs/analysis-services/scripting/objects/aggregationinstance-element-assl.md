---
title: Элемент AggregationInstance (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AggregationInstance Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- AggregationInstance element
ms.assetid: 2e77e9e1-9f2c-4df4-9aa6-5b7b911016a3
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bc7568cb3904dec582306144b705fe3c6b2f06ca
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>Замечания  
 Если в элементе [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md) используется элемент [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) для создания агрегатов применительно к этой секции, для каждого объекта [Aggregation](../../../analysis-services/scripting/objects/aggregation-element-assl.md) в схеме **AggregationDesign** создается экземпляр для этой секции. В одной и той же статистической схеме может использоваться несколько секций для создания нескольких экземпляров определенного агрегата. Элемент **AggregationInstance** представляет экземпляр определенного статистического вычисления.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>См. также  
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
