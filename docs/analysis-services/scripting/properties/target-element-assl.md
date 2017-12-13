---
title: "Целевой элемент (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Target Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Target
helpviewer_keywords: Target element
ms.assetid: 08ce0441-94b6-4f1d-acba-f31c8212cb79
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1b84d58d379a74de7efcce2f10eeb008a57449de
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="target-element-assl"></a>Элемент Target (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет цель элемента [действия](../../../analysis-services/scripting/objects/action-element-assl.md) элемента.  
  
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
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Действие](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Ожидаемое значение этого элемента зависит от значения [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md) для родителя **действия**. В следующей таблице описаны ожидаемые значения **Target** , основанные на значении **TargetType**.  
  
|Значение TargetType|Ожидаемое значение|  
|----------------------|--------------------|  
|*Cube*|Имя куба.|  
|*Ячейки*|Выражение вложенного куба.|  
|*Набор*|Выражение набора или имя именованного набора.<br /><br /> Примечание: Нельзя использовать инструкции подзапроса выборки.|  
|*Иерархия, HierarchyMembers*|Имя иерархии.|  
|*Измерение, DimensionMembers*|Имя измерения.|  
|*Уровень LevelMembers*|Имя уровня.|  
|*Атрибут AttributeMembers*|Имя атрибута.|  
  
 Элемент, соответствующий родителю параметра **целевой** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
