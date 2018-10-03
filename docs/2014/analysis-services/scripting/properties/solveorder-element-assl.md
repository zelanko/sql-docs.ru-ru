---
title: Элемент SolveOrder (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- SolveOrder Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SolveOrder
helpviewer_keywords:
- SolveOrder element
ms.assetid: ec43e055-97dd-4f2a-9a7c-2df2e1119e56
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4fbd4132a0dc27d9055956d4b49a1ad02bc5dff5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219514"
---
# <a name="solveorder-element-assl"></a>Элемент SolveOrder (ASSL)
  Указывает порядок вычисления, в котором [CalculationProperty](../objects/calculationproperty-element-assl.md) элемент применяется к вычисляемым элементам или вычисляемым определениям ячеек.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CalculationProperty>  
   ...  
   <SolveOrder>...</SolveOrder>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[CalculationProperty](../objects/calculationproperty-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 `SolveOrder` Свойство применяется к `CalculationProperty` элементов при помощи [CalculationType](calculationtype-element-assl.md) из *член* или *ячеек*.  
  
 Элемент, соответствующий родителю параметра `SolveOrder` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CalculationProperties &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Элемент MdxScripts &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
