---
title: Элемент AggregateFunction (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregateFunction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregateFunction
helpviewer_keywords:
- AggregateFunction element
ms.assetid: 880b6bd0-d62a-4221-831c-39f748ee84f2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5c40f1767de94515d11229e5dce13f6cb94c9334
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055314"
---
# <a name="aggregatefunction-element-assl"></a>Элемент AggregateFunction (ASSL)
  Определяет тип агрегатной функции, используемые [мер](../objects/measure-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Measure>  
   ...  
   <AggregateFunction>...</AggregateFunction>  
   ...  
</Measure>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Sum*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Меры](../objects/measure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Sum*|Статистическая обработка этой меры выполняется с помощью функции `Sum`.|  
|*число*|Статистическая обработка этой меры выполняется с помощью функции `Count`.|  
|*Min*|Статистическая обработка этой меры выполняется с помощью функции `Min`.|  
|*Max*|Статистическая обработка этой меры выполняется с помощью функции `Max`.|  
|*DistinctCount*|Статистическая обработка этой меры выполняется с помощью функции `DistinctCount`.|  
|*None*|Статистическая обработка этой меры не выполняется.|  
|*ByAccount*|Статистическая обработка этой меры выполняется по типу счета.|  
|*AverageOfChildren*|Статистическая обработка этой меры выполняется путем возвращения среднего значения ее потомков.|  
|*FirstChild*|Статистическая обработка этой меры выполняется путем возвращения ее первого дочернего элемента.|  
|*LastChild*|Статистическая обработка этой меры выполняется путем возвращения ее последнего дочернего элемента.|  
|*FirstNonEmpty*|Статистическая обработка этой меры выполняется путем возвращения ее первого непустого элемента.|  
|*LastNonEmpty*|Статистическая обработка этой меры выполняется путем возвращения ее последнего непустого элемента.|  
  
 Перечисление, соответствующее допустимым значениям элемента `AggregateFunction` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
