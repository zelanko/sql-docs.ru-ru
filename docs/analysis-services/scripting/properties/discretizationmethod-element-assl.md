---
title: "Элемент DiscretizationMethod (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DiscretizationMethod Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DiscretizationMethod
helpviewer_keywords:
- DiscretizationMethod element
ms.assetid: 4cfe015f-ad6c-47e1-8aff-c9c7677867b1
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e2bbf548ba16ccc81d1536c5c64a22e9c69d96d1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="discretizationmethod-element-assl"></a>Элемент DiscretizationMethod (ASSL)
  Определяет метод дискретизации.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationMethod>...</DiscretizationMethod>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*None*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значение элемента **DiscretizationMethod** определяет, как выполняется дискретизация значений для элементов **DimensionAttribute** или **ScalarMiningStructureColumn** , либо организация в виде конкретного набора групп. Дополнительные сведения о методах дискретизации см. в разделе [методы дискретизации &#40; интеллектуального анализа данных &#41;](../../../analysis-services/data-mining/discretization-methods-data-mining.md).  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Автоматически*|Эквивалентен методу дискретизации AUTOMATIC для столбцов структуры интеллектуального анализа данных.|  
|*EqualAreas*|Эквивалентен методу дискретизации EQUAL_AREAS для столбцов структуры интеллектуального анализа данных.|  
|*Кластеры*|Эквивалентен методу дискретизации CLUSTERS для столбцов структуры интеллектуального анализа данных.|  
|*Пороги*|Эквивалентен методу дискретизации THRESHOLDS для столбцов структуры интеллектуального анализа данных.|  
|*EqualRanges*|Эквивалентен методу дискретизации EQUAL_RANGES для столбцов структуры интеллектуального анализа данных.|  
  
 Перечисление, соответствующее разрешенным значениям для **DiscretizationMethod** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DiscretizationMethod>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

