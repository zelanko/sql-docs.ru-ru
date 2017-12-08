---
title: "Введите элемент (PerspectiveCalculation) (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Type Element (PerspectiveCalculation)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TYPE
helpviewer_keywords: Type element
ms.assetid: d7b87aea-3265-4f3c-a7ee-4f3e90f9a0b7
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 25d291aa367e890c761de46f00880c3a6a626632
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="type-element-perspectivecalculation-assl"></a>Type, элемент (PerspectiveCalculation) (ASSL)
  Указывает тип [PerspectiveCalculation](../../../analysis-services/scripting/data-type/perspectivecalculation-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<PerspectiveCalculation>  
   ...  
   <Type>...</Type>  
   ...  
</PerspectiveCalculation>  
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
|Родительский элемент|[PerspectiveCalculation](../../../analysis-services/scripting/data-type/perspectivecalculation-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Член*|вычисляемый элемент|  
|*Набор*|Именованный набор|  
  
 Перечисление, соответствующее разрешенным значениям для **тип** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.PerspectiveCalculationType>.  
  
 Элемент, соответствующий родителю параметра **тип** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.PerspectiveCalculation>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
