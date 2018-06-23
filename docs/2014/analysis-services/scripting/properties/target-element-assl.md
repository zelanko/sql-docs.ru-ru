---
title: Целевой элемент (ASSL) | Документы Microsoft
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
- Target Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Target
helpviewer_keywords:
- Target element
ms.assetid: 08ce0441-94b6-4f1d-acba-f31c8212cb79
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 65150d66769a2ebdb67609989efbc1a7f81e9f89
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095294"
---
# <a name="target-element-assl"></a>Элемент Target (ASSL)
  Определяет цель элемента [действия](../objects/action-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action>  
   ...  
   <Target>...</Target>  
   ...  
</Action>  
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
|Родительский элемент|[Действие](../objects/action-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Ожидаемое значение этого элемента зависит от значения [TargetType](targettype-element-assl.md) для родителя `Action`. В следующей таблице описаны ожидаемые значения `Target`, основанные на значении `TargetType`.  
  
|Значение TargetType|Ожидаемое значение|  
|----------------------|--------------------|  
|*Cube*|Имя куба.|  
|*Ячейки*|Выражение вложенного куба.|  
|*набор*|Выражение набора или имя именованного набора. **Примечание:** инструкции подзапроса выборки не может использоваться.|  
|*Иерархия, HierarchyMembers*|Имя иерархии.|  
|*Измерение, DimensionMembers*|Имя измерения.|  
|*Уровень LevelMembers*|Имя уровня.|  
|*Атрибут AttributeMembers*|Имя атрибута.|  
  
 Элемент, соответствующий родителю параметра `Target` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  