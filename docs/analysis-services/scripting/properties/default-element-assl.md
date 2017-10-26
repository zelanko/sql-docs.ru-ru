---
title: "По умолчанию элемент (ASSL) | Документы Microsoft"
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
- Default Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DEFAULT
helpviewer_keywords:
- Default element
ms.assetid: 02c1844c-51fb-44fe-aafb-001e53ad293c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2eb9c10eb6c257c7db6f97311b05360931204698
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="default-element-assl"></a>Элемент Default (ASSL)
  Определяет, является ли [DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md) является действием детализации по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DrillThroughAction>  
   ...  
   <Default>...</Default  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Boolean|  
|Значение по умолчанию|**False**|  
|Количество элементов|0—1: необязательный элемент, который появляется только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **по умолчанию** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DrillThroughAction>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

