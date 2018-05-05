---
title: Элемент AggregationFunction (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
manager: kfile
ms.openlocfilehash: c7c9aedc12abbeb5ab805e0d85cfe1421857749b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="aggregationfunction-element-assl"></a>Элемент AggregationFunction (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Значение|Описание|  
|-----------|-----------------|  
|*Sum*|Статистическая обработка этой меры выполняется с помощью функции **Sum** .|  
|*Count*|Статистическая обработка этой меры выполняется с помощью функции **Count** .|  
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
  
## <a name="see-also"></a>См. также  
 [Учетные записи элемента &#40;ASSL&#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
