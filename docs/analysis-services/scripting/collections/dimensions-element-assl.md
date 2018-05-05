---
title: Измерения элемента (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
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
- Dimensions Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Dimensions
helpviewer_keywords:
- Dimensions element
ms.assetid: 104e3154-92e9-4c6b-9cf3-e3f3fc712b28
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d26e194155f0c9ae1be102116bb8d2a1bfa4808c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="dimensions-element-assl"></a>Элемент Dimensions (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит коллекцию измерений, связанных с родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Database> <!-- or Aggregation, AggregationDesign, AggregationInstance, Cube, MeasureGroup, Perspective -->  
   ...  
   <Dimensions>  
      <Dimension>...</Dimension>  
   </Dimensions>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Агрегат](../../../analysis-services/scripting/objects/aggregation-element-assl.md), [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md), [AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md), [куба](../../../analysis-services/scripting/objects/cube-element-assl.md), [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md), [ Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md)|  
|Дочерние элементы|[Измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.DimensionCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
