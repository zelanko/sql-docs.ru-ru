---
title: Элемент KeyColumn (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- KeyColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyColumn
helpviewer_keywords:
- KeyColumn element
ms.assetid: 7b03eeb3-d478-4c38-822e-8cdfcc485039
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7594a92eb8c2eb4cdb423c7298bc3929dc49dc32
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098040"
---
# <a name="keycolumn-element-assl"></a>Элемент KeyColumn (ASSL)
  Содержит определение столбца, который является ключевым или входит в состав ключа для атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<KeyColumns>  
   <KeyColumn xsi:type="DataItem">...</KeyColumn>  
<KeyColumns>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|1-N: обязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[KeyColumns](../collections/columns-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о `DataItem` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) и свойства `DataItem` введите см. в разделе [DataItem, тип данных &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 В модели объектов AMO родителям коллекции `KeyColumns` соответствуют элементы <xref:Microsoft.AnalysisServices.AggregationInstanceAttribute>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, <xref:Microsoft.AnalysisServices.MeasureGroupAttribute> и <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных AggregationInstanceAttribute &#40;ASSL&#41;](../data-type/aggregationinstanceattribute-data-type-assl.md)   
 [Тип данных AggregationInstanceCubeDimension &#40;ASSL&#41;](../data-type/dimension-data-type-assl.md)   
 [Тип данных DimensionAttribute &#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [Тип данных MeasureGroupAttribute &#40;ASSL&#41;](../data-type/measuregroupattribute-data-type-assl.md)   
 [Тип данных ScalarMiningStructureColumn &#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  