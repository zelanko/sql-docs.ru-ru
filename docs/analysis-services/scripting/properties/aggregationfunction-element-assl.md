---
title: "Элемент AggregationFunction (ASSL) | Документы Microsoft"
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
- AggregationFunction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationFunction
helpviewer_keywords:
- AggregationFunction element
ms.assetid: 40cfc7f9-1089-45f9-be90-a29770ed9682
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e14f744b35fc1d48ba2a96b15bd8bc3ec46e8e20
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="aggregationfunction-element-assl"></a>Элемент AggregationFunction (ASSL)
  Содержит статистическую функцию, используемую для типа счета.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Account>  
   ...  
   <AggregationFunction>...</AggregationFunction>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Sum*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Учетная запись](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из следующих строк.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Sum*|Статистическая обработка этой меры выполняется с помощью функции **Sum** .|  
|*Счетчик*|Статистическая обработка этой меры выполняется с помощью функции **Count** .|  
|*Min*|Статистическая обработка этой меры выполняется с помощью функции **Min** .|  
|*Max*|Статистическая обработка этой меры выполняется с помощью функции **Max** .|  
|*DistinctCount*|Статистическая обработка этой меры выполняется с помощью функции **DistinctCount** .|  
|*None*|Статистическая обработка этой меры не выполняется.|  
|*AverageOfChildren*|Статистическая обработка этой меры выполняется путем возвращения среднего значения ее потомков.|  
|*FirstChild*|Статистическая обработка этой меры выполняется путем возвращения ее первого дочернего элемента.|  
|*LastChild*|Статистическая обработка этой меры выполняется путем возвращения ее последнего дочернего элемента.|  
|*FirstNonEmpty*|Статистическая обработка этой меры выполняется путем возвращения ее первого непустого элемента.|  
|*LastNonEmpty*|Статистическая обработка этой меры выполняется путем возвращения ее последнего непустого элемента.|  
  
 Перечисление, соответствующее разрешенным значениям для **AggregationFunction** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Accounts &#40; ASSL &#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

