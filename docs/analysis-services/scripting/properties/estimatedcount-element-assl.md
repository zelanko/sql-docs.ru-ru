---
title: Элемент EstimatedCount (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 79714d82276a6ad846d5b1a03e60a05063dc8461
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="estimatedcount-element-assl"></a>Элемент EstimatedCount (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит ожидаемое число элементов атрибута, определенное пользователем.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationDesignAttribute> <!-- or DimensionAttribute -->  
      ...  
   <EstimatedCount>...</EstimatedCount>  
   ...  
</AggregationDesignAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Long|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AggregationDesignAttribute](../../../analysis-services/scripting/data-type/aggregationdesignattribute-data-type-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Это значение назначается пользователем и используется [элемент AggregationDesign &#40;ASSL&#41;](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md).  
  
 Элементы, соответствующие родителям элемента **EstimatedCount** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AggregationDesignAttribute> и <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
