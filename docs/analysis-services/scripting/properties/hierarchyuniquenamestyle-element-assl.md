---
title: Элемент HierarchyUniqueNameStyle (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 642f59f4e6946c47a2c912e9a24b7ee796449b54
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="hierarchyuniquenamestyle-element-assl"></a>Элемент HierarchyUniqueNameStyle (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет, каким образом уникальные имена формируются для иерархий, содержащихся в [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeDimension>  
   ...  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*IncludeDimensionName*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*IncludeDimensionName*|Имя измерения включается в качестве части имени иерархии.|  
|*ExcludeDimensionName*|Имя измерения не включается в качестве части имени иерархии.|  
  
 Элемент, соответствующий родителю параметра **HierarchyUniqueNameStyle** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CUBE & #40; ASSL & #41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Элемент измерения & #40; ASSL & #41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
