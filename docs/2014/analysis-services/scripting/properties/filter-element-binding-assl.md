---
title: Элемент filter (Binding) (ASSL) | Документы Microsoft
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
- Filter Element (Binding)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- filter
helpviewer_keywords:
- Filter element
ms.assetid: 3d4cd169-2903-4266-8541-540ece424b7b
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 659719ea4ba87b548b08b5b7cb680e1b28b563d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193459"
---
# <a name="filter-element-binding-assl"></a>Элемент Filter (Binding) (ASSL)
  Содержит многомерное выражение, фильтрующее содержание родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeDimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <Filter>...</Filter>  
   ...  
</CubeDimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CubeDimensionBinding](../data-type/binding-data-type-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о `Binding` типа, включая таблицы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] объектов языка сценариев (ASSL) `Binding` тип и иерархию наследования `Binding` типов, в разделе [тип привязки данных &#40;ASSL &#41;](../data-type/binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Элементы, соответствующие родителям элемента `Filter` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CubeDimensionBinding> и <xref:Microsoft.AnalysisServices.MeasureGroupBinding>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных Binding &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [Источники данных и привязки &#40;многомерные службы SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  