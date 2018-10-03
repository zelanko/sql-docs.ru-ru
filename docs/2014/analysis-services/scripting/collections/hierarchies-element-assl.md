---
title: Элемент hierarchies (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Hierarchies Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Hierarchies
helpviewer_keywords:
- Hierarchies element
ms.assetid: dc844eea-869c-4217-b9be-e543a76f5e92
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4b9e8fa5c67d3b4b9b00be7c7517307f911327db
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129016"
---
# <a name="hierarchies-element-assl"></a>Элемент Hierarchies (ASSL)
  Содержит коллекцию элементов [иерархии](../objects/hierarchy-element-assl.md) элементы, связанные с родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension> <!-- or CubeDimension, PerspectiveDimension -->  
   ...  
   <Hierarchies>  
            <Hierarchy>...</Hierarchy> <!-- parent: Dimension -->  
      <!-- or -->  
      <Hierarchy xsi:type="CubeHierarchy">...</Hierarchy> <!-- parent: CubeDimension -->  
     <!-- or -->  
      <Hierarchy xsi:type="PerspectiveHierarchy">...</Hierarchy> <!-- parent: PerspectiveDimension -->  
   <Hierarchies>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CubeDimension](../data-type/dimension-data-type-assl.md), [измерения](../objects/dimension-element-assl.md), [PerspectiveDimension](../data-type/perspectivedimension-data-type-assl.md)|  
  
|Предок или родитель|Дочерний элемент|  
|------------------------|-------------------|  
|[CubeDimension](../data-type/dimension-data-type-assl.md)|[Иерархия](../objects/hierarchy-element-assl.md) типа [CubeHierarchy](../data-type/hierarchy-data-type-assl.md)|  
|[Dimension](../objects/dimension-element-assl.md)|[Hierarchy](../objects/hierarchy-element-assl.md)|  
|[PerspectiveDimension](../data-type/perspectivedimension-data-type-assl.md)|[Иерархия](../objects/hierarchy-element-assl.md) типа [PerspectiveHierarchy](../data-type/perspectivehierarchy-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующие элементы в модели объектов AMO — это <xref:Microsoft.AnalysisServices.HierarchyCollection>, <xref:Microsoft.AnalysisServices.CubeHierarchyCollection> и <xref:Microsoft.AnalysisServices.PerspectiveHierarchyCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
