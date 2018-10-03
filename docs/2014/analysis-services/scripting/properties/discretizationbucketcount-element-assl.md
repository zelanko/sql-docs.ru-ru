---
title: Элемент DiscretizationBucketCount (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DiscretizationBucketCount Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DiscretizationBucketCount
helpviewer_keywords:
- DiscretizationBucketCount element
ms.assetid: 551a73ae-59e1-4079-a2d9-988df96b5e07
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5fea5841750555185cbeb40f99b9dc5d312be490
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202164"
---
# <a name="discretizationbucketcount-element-assl"></a>Элемент DiscretizationBucketCount (ASSL)
  Содержит количество сегментов дискретизации.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationBucketCount>...</DiscretizationBucketCount>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение элемента `DiscretizationBucketCount` определяет количество групп или сегментов, создаваемых при дискретизации значений `DimensionAttribute` или `ScalarMiningStructureColumn` или их организации в конкретный набор групп. Если этот элемент не указан или если указано нулевое значение для значения элемента [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] создает достаточное количество групп зависит от метода дискретизации. Дополнительные сведения о методах дискретизации см. в разделе [методы дискретизации &#40;интеллектуального анализа данных&#41;](../../data-mining/discretization-methods-data-mining.md).  
  
 Элементы, соответствующие родителям элемента `DiscretizationBucketCount` в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.DimensionAttribute> и <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также  
 [Элемент DiscretizationMethod &#40;ASSL&#41;](discretizationmethod-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
