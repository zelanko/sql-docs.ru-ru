---
title: "Элемент AllMemberAggregationUsage (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AllMemberAggregationUsage Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AllMemberAggregationUsage
helpviewer_keywords:
- AllMemberAggregationUsage element
ms.assetid: 264fe9d8-8e9a-4642-8cee-7c2804126926
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7914e17c2dbb0430078d3f5cc8d728779a54c6be
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="allmemberaggregationusage-element-assl"></a>Элемент AllMemberAggregationUsage (ASSL)
  Элементы управления как конструктор статистических схем в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] статистических схем.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeDimension>  
   ...  
   <AllMemberAggregationUsage>...</AllMemberAggregationUsage>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*По умолчанию*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Полный*|Каждый агрегат для куба должен включать элемент «Все».|  
|*None*|Никакой агрегат для куба не должен включать элемент «Все».|  
|*Без ограничений*|На конструктор статистических схем не налагаются никакие ограничения.|  
|*По умолчанию*|Эквивалентно *Unrestricted*.|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **AllMemberAggregationUsage** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент CUBE &#40; ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Элемент измерения &#40; ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

