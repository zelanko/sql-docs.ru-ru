---
title: Элемент MeasureID (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c206e2e8aa9d7aed986077cd63879f832374d33d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="measureid-element-assl"></a>Элемент MeasureID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Связывает [мер](../../../analysis-services/scripting/objects/measure-element-assl.md) элемента с родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureBinding> <!-- or AggregationInstanceMeasure, PerspectiveMeasure -->  
   ...  
   <MeasureID>...</MeasureID>  
   ...  
</MeasureBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AggregationInstanceMeasure](../../../analysis-services/scripting/data-type/aggregationinstancemeasure-data-type-assl.md), [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md), [PerspectiveMeasure](../../../analysis-services/scripting/data-type/perspectivemeasure-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элементы, соответствующие родителям элемента **MeasureID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AggregationInstanceMeasure>, <xref:Microsoft.AnalysisServices.MeasureBinding>, и <xref:Microsoft.AnalysisServices.PerspectiveMeasure>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
