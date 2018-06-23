---
title: Элемент Hierarchy (ASSL) | Документы Microsoft
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
- Hierarchy Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Hierarchy
helpviewer_keywords:
- Hierarchy element
ms.assetid: ac54d74a-5e6c-4c24-83bf-766440478f6c
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6c5acacc00f072f50cc0429c345b5a2fedc6afc6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192981"
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
|Тип данных и длина||  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="data-type-and-length"></a>Тип данных и длина  
  
|Предок или родитель|Тип данных|  
|------------------------|---------------|  
|[Dimension](../data-type/hierarchy-data-type-assl.md)|  
|[CubeDimension](../data-type/cubehierarchy-data-type-assl.md)|  
|[PerspectiveDimension](../data-type/perspectivehierarchy-data-type-assl.md)|  
|[RegularMeasureGroupDimension](../data-type/measuregrouphierarchy-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Иерархии](../collections/hierarchies-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Соответствующие элементы в модели объектов AMO — это <xref:Microsoft.AnalysisServices.Hierarchy>, <xref:Microsoft.AnalysisServices.CubeHierarchy> и <xref:Microsoft.AnalysisServices.PerspectiveHierarchy>.  
  
## <a name="see-also"></a>См. также  
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  