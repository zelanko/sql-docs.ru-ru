---
title: Целевой элемент (ASSL) | Документация Майкрософт
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 98ec5c729f5735343f5eaa87e5232fcfb138cf38
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38045782"
---
# <a name="target-element-assl"></a>Элемент Target (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет цель элемента [действие](../../../analysis-services/scripting/objects/action-element-assl.md) элемент.  
  
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
|Родительский элемент|[Действие](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Ожидаемое значение этого элемента зависит от значения [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md) для родителя **действие**. В следующей таблице описаны ожидаемые значения **Target** , основанные на значении **TargetType**.  
  
|Значение TargetType|Ожидаемое значение|  
|----------------------|--------------------|  
|*Cube*|Имя куба.|  
|*Ячейки*|Выражение вложенного куба.|  
|*Набор*|Выражение набора или имя именованного набора.<br /><br /> Примечание: Нельзя использовать инструкцию подзапроса выборки.|  
|*Иерархия, HierarchyMembers*|Имя иерархии.|  
|*Измерение, DimensionMembers*|Имя измерения.|  
|*Уровень, LevelMembers*|Имя уровня.|  
|*Атрибут, AttributeMembers*|Имя атрибута.|  
  
 Элемент, соответствующий родителю параметра **целевой** в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
