---
title: "Элемент OverrideBehavior (ASSL) | Документы Microsoft"
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
- OverrideBehavior Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- OverrideBehavior element
ms.assetid: 6a5b361a-6061-4b73-b1a7-1237fb77606c
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fb4c90ea4c5fe289cf6a0539018a24f99dafd991
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="overridebehavior-element-assl"></a>Элемент OverrideBehavior (ASSL)
  Указывает на переопределения связи, описываемого [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <OverrideBehavior>...</OverrideBehavior>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Strong*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент **OverrideBehavior** определяет, как позиционирование связанного атрибута влияет на позиционирование самого атрибута.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Strong*|Указывает на переопределения связи, задаваемой элементом AttributeRelationship. Указывает, как позиционирование одного атрибута влияет на позицию другого.|  
|*None*|Не влияет.|  
  
 Перечисление, соответствующее разрешенным значениям для **OverrideBehavior** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.OverrideBehavior>.  
  
## <a name="see-also"></a>См. также:  
 [Атрибуты и иерархии атрибутов](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

