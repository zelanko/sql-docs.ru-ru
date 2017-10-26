---
title: "Элемент FiscalFirstDayOfMonth (ASSL) | Документы Microsoft"
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
- FiscalFirstDayOfMonth Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- FiscalFirstDayOfMonth
helpviewer_keywords:
- FiscalFirstDayOfMonth element
ms.assetid: f793e93f-62de-4c3b-90b0-a46bd3cadae5
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6fece15df5499d98722bd2af1760c3da6233e928
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="fiscalfirstdayofmonth-element-assl"></a>Элемент FiscalFirstDayOfMonth (ASSL)
  Определяет первый день финансового месяца для [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<TimeBinding>  
   ...  
   <FiscalFirstDayOfMonth>...</FiscalFirstDayOfMonth>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целое число (от 1 до 31)|  
|Значение по умолчанию|**1**|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **FiscalFirstDayOfMonth** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.TimeBinding>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

