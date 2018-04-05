---
title: Элемент filter (Binding) (ASSL) | Документы Microsoft
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
- Filter Element (Binding)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- filter
helpviewer_keywords:
- Filter element
ms.assetid: 3d4cd169-2903-4266-8541-540ece424b7b
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a1da8dd5c06124446589cd0c084c0ba7d19efca7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="filter-element-binding-assl"></a>Элемент Filter (Binding) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит выражение многомерных выражений (MDX), которое фильтрует содержимое родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeDimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <Filter>...</Filter>  
   ...  
</CubeDimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Дополнительные сведения о **привязки** типа, включая таблицы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] объектов языка сценариев (ASSL) **привязки** тип и иерархию наследования **привязки**  типов, в разделе [тип привязки данных &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [&#40; источники данных и привязки Многомерные службы SSAS &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Элементы, соответствующие родителям элемента **фильтра** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CubeDimensionBinding> и <xref:Microsoft.AnalysisServices.MeasureGroupBinding>.  
  
## <a name="see-also"></a>См. также:  
 [Тип привязки данных &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Источники данных и привязки &#40; Многомерные службы SSAS &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
