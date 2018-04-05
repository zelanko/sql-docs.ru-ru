---
title: Элемент ActionID (ASSL) | Документы Microsoft
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
- ActionID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ActionID
helpviewer_keywords:
- ActionID element
ms.assetid: 2c9c66b2-a7ea-4874-a0ed-020ce3feab20
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 508a4fce7624979dac8e8180a5e8cfe070682db0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="actionid-element-assl"></a>Элемент ActionID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит имя [действия](../../../analysis-services/scripting/objects/action-element-assl.md) элемент, определенный на [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента, которое станет доступным в [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md) элемент как [PerspectiveAction](../../../analysis-services/scripting/data-type/perspectiveaction-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<PerspectiveAction>  
   <ActionID>...</ActionID  
</PerspectiveAction>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[PerspectiveAction](../../../analysis-services/scripting/data-type/perspectiveaction-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Элемент, соответствующий родителю параметра **ActionID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.PerspectiveAction>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Actions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/actions-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
