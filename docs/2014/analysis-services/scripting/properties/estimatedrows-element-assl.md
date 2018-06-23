---
title: Элемент EstimatedRows (ASSL) | Документы Microsoft
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
- EstimatedRows Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EstimatedRows
helpviewer_keywords:
- EstimatedRows element
ms.assetid: 08a66481-6479-4a93-aa7e-15e8b1f854f2
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0348e39cf3528c34028677a22c2bf7ec25697705
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187817"
---
# <a name="estimatedrows-element-assl"></a>Элемент EstimatedRows (ASSL)
  Содержит ожидаемое число строк, представленных родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationDesign> <!-- or Cube, MeasureGroup, MeasureGroupBinding, Partition -->  
   ...  
   <EstimatedRows>...</EstimatedRows>  
   ...  
</AggregationDimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Long|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AggregationDesign](../objects/aggregationdesign-element-assl.md), [куба](../objects/cube-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MeasureGroupBinding](../data-type/binding-data-type-assl.md), [секции](../objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элементы, соответствующие родителям элемента `EstimatedRows` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.AggregationDesign>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.MeasureGroup>, <xref:Microsoft.AnalysisServices.MeasureGroupBinding> и <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  