---
title: Элемент ActionID (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ActionID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ActionID
helpviewer_keywords:
- ActionID element
ms.assetid: 2c9c66b2-a7ea-4874-a0ed-020ce3feab20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ebbb9a3d62501703b00ec07095f58a51434f84b0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104834"
---
# <a name="actionid-element-assl"></a>Элемент ActionID (ASSL)
  Содержит имя [действие](../objects/action-element-assl.md) элемент, определенный на [куба](../objects/cube-element-assl.md) элемента, которая становится доступной в [перспективы](../objects/perspective-element-assl.md) элемент как [PerspectiveAction](../data-type/action-data-type-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<PerspectiveAction>  
   <ActionID>...</ActionID  
</PerspectiveAction>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[PerspectiveAction](../data-type/action-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `ActionID` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.PerspectiveAction>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Actions &#40;ASSL&#41;](../collections/actions-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
