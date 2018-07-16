---
title: Элемент DiscretizationMethod (ASSL) | Документация Майкрософт
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
- DiscretizationMethod Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DiscretizationMethod
helpviewer_keywords:
- DiscretizationMethod element
ms.assetid: 4cfe015f-ad6c-47e1-8aff-c9c7677867b1
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6347db0e5d964b10112516b4c607a5185f247b65
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253006"
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение элемента `DiscretizationMethod` определяет, как выполняется дискретизация значений для элементов `DimensionAttribute` или `ScalarMiningStructureColumn`, либо организация в виде конкретного набора групп. Дополнительные сведения о методах дискретизации см. в разделе [методы дискретизации &#40;интеллектуального анализа данных&#41;](../../data-mining/discretization-methods-data-mining.md).  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Автоматически*|Эквивалентен методу дискретизации AUTOMATIC для столбцов структуры интеллектуального анализа данных.|  
|*EqualAreas*|Эквивалентен методу дискретизации EQUAL_AREAS для столбцов структуры интеллектуального анализа данных.|  
|*Кластеры*|Эквивалентен методу дискретизации CLUSTERS для столбцов структуры интеллектуального анализа данных.|  
|*Пороги*|Эквивалентен методу дискретизации THRESHOLDS для столбцов структуры интеллектуального анализа данных.|  
|*EqualRanges*|Эквивалентен методу дискретизации EQUAL_RANGES для столбцов структуры интеллектуального анализа данных.|  
  
 Перечисление, соответствующее допустимым значениям элемента `DiscretizationMethod` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.DiscretizationMethod>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
