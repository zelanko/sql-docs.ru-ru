---
title: Целевой элемент (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 23d55d909179fd568075feba54199514a7396c6b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169064"
---
# <a name="target-element-assl"></a>Элемент Target (ASSL)
  Определяет цель элемента [действие](../objects/action-element-assl.md) элемент.  
  
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
|*Набор*|Выражение набора или имя именованного набора. **Примечание:** нельзя использовать инструкцию подзапроса выборки.|  
|*Иерархия, HierarchyMembers*|Имя иерархии.|  
|*Измерение, DimensionMembers*|Имя измерения.|  
|*Уровень, LevelMembers*|Имя уровня.|  
|*Атрибут, AttributeMembers*|Имя атрибута.|  
  
 Элемент, соответствующий родителю параметра `Target` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
