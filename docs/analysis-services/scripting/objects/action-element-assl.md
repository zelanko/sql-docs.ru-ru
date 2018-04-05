---
title: Элемент Action (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Action Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Action
helpviewer_keywords:
- Action element
ms.assetid: aaee06a2-91c6-4007-b787-79cb08d63c77
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 80a0bdc56107980b9865015f07abd8b213d1021c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="action-element-assl"></a>Элемент Action (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит сведения о действии, доступном в [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемент или [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Actions>  
   <Action xsi:type="DrillThroughAction">...</Action> <!-- ancestor: Cube -->  
   <Action xsi:type="ReportAction">...</Action> <!-- ancestor: Cube -->  
   <Action xsi:type="StandardAction">...</Action> <!-- ancestor: Cube -->  
   <!-- or -->  
   <Action xsi:type="PerspectiveAction">...</Action> <!-- ancestor: Perspective -->  
</Actions>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|См. в следующей таблице.|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
|Предок или родитель|Тип данных|  
|------------------------|---------------|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|[DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md), [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md), [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
|[Перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md)|[PerspectiveAction](../../../analysis-services/scripting/data-type/perspectiveaction-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Действия](../../../analysis-services/scripting/collections/actions-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент CUBE &#40; ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Элемент perspective &#40; ASSL &#41;](../../../analysis-services/scripting/objects/perspective-element-assl.md)   
 [Тип данных PerspectiveAction &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/perspectiveaction-data-type-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
