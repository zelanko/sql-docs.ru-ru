---
title: "Элемент TargetType (ASSL) | Документы Microsoft"
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
- TargetType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TargetType
helpviewer_keywords:
- TargetType element
ms.assetid: 2c69ea6e-2af7-435b-9841-86117d5554a7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 49c2fd13925130bfb76730708775f6bb0d5e79ca
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="targettype-element-assl"></a>Элемент TargetType (ASSL)
  Определяет тип элемента, определенного в [целевой](../../../analysis-services/scripting/properties/target-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action>  
   ...  
   <TargetType>...</TargetType>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Действие](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Cube*|Целью действия является куб.|  
|*Ячейки*|Целью действия является вложенный куб.|  
|*Набор*|Целью действия является набор.|  
|*Hierarchy*|Целью действия является иерархия.|  
|*Level*|Целью действия является уровень.|  
|*DimensionMembers*|Целью действия является элементы измерения.|  
|*HierarchyMembers*|Целью действия является элементы иерархии.|  
|*LevelMembers*|Целью действия является элементы уровня.|  
|*AttributeMembers*|Целью действия является элементы атрибута.|  
  
 Перечисление, соответствующее разрешенным значениям для **TargetType** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ActionTargetType>.  
  
 Элемент, соответствующий родителю параметра **TargetType** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
