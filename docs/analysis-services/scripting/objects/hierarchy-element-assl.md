---
title: "Элемент Hierarchy (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Hierarchy Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Hierarchy
helpviewer_keywords: Hierarchy element
ms.assetid: ac54d74a-5e6c-4c24-83bf-766440478f6c
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 49265caaf75b32c5ebf7c69fb84e7a7dab69fc57
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="hierarchy-element-assl"></a>Элемент Hierarchy (ASSL)
  Определяет иерархию в измерении.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Hierarchies>  
   <Hierarchy xsi:type="Hierarchy">...</Hierarchy> <!-- ancestor: Dimension -->  
   <!-- or -->  
   <Hierarchy xsi:type="CubeHierarchy">...</Hierarchy> <!-- ancestor: CubeDimension -->  
   <!-- or -->  
   <Hierarchy xsi:type="PerspectiveHierarchy">...</Hierarchy> <!-- ancestor: PerspectiveDimension -->  
   <!-- or -->  
   <Hierarchy xsi:type="MeasureGroupHierarchy">...</Hierarchy> <!-- ancestor: RegularMeasureGroupDimension -->  
</Hierarchies>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|См. в следующей таблице.|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
|Предок или родитель|Тип данных|  
|------------------------|---------------|  
|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|[Hierarchy](../../../analysis-services/scripting/data-type/hierarchy-data-type-assl.md)|  
|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|[CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)|  
|[PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md)|[PerspectiveHierarchy](../../../analysis-services/scripting/data-type/perspectivehierarchy-data-type-assl.md)|  
|[RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md)|[MeasureGroupHierarchy](../../../analysis-services/scripting/data-type/measuregrouphierarchy-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Иерархии](../../../analysis-services/scripting/collections/hierarchies-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Соответствующие элементы в модели объектов AMO — это <xref:Microsoft.AnalysisServices.Hierarchy>, <xref:Microsoft.AnalysisServices.CubeHierarchy> и <xref:Microsoft.AnalysisServices.PerspectiveHierarchy>.  
  
## <a name="see-also"></a>См. также:  
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
