---
title: Элемент AggregateFunction (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f0b499b81d8c29c51cc086127bad8749ee089120
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="aggregatefunction-element-assl"></a>Элемент AggregateFunction (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет тип агрегатной функции, используемой [мер](../../../analysis-services/scripting/objects/measure-element-assl.md) элемента.  
  
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Меры](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Sum*|Статистическая обработка этой меры выполняется с помощью функции **Sum** .|  
|*Count*|Статистическая обработка этой меры выполняется с помощью функции **Count** .|  
|*Min*|Статистическая обработка этой меры выполняется с помощью функции **Min** .|  
|*Max*|Статистическая обработка этой меры выполняется с помощью функции **Max** .|  
|*DistinctCount*|Статистическая обработка этой меры выполняется с помощью функции **DistinctCount** .|  
|*None*|Статистическая обработка этой меры не выполняется.|  
|*ByAccount*|Статистическая обработка этой меры выполняется по типу счета.|  
|*AverageOfChildren*|Статистическая обработка этой меры выполняется путем возвращения среднего значения ее потомков.|  
|*FirstChild*|Статистическая обработка этой меры выполняется путем возвращения ее первого дочернего элемента.|  
|*LastChild*|Статистическая обработка этой меры выполняется путем возвращения ее последнего дочернего элемента.|  
|*FirstNonEmpty*|Статистическая обработка этой меры выполняется путем возвращения ее первого непустого элемента.|  
|*LastNonEmpty*|Статистическая обработка этой меры выполняется путем возвращения ее последнего непустого элемента.|  
  
 Перечисление, соответствующее разрешенным значениям для **AggregateFunction** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
