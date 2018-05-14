---
title: Элемент ProcessingMode (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a24e90bca2ff88fc11d5bd4f33bf10bd3b5efae2
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="processingmode-element-assl"></a>Элемент ProcessingMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет, следует ли экземпляру производить индексирование и статистическую обработку во время работы или после нее.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <ProcessingMode>...</ProcessingMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Regular*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Куб](../../../analysis-services/scripting/objects/cube-element-assl.md), [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [секции](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение **ProcessingMode** элемента **Cube** предоставляет значения по умолчанию для куба и может переопределяться установкой **ProcessingMode** для каждой секции.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Regular*|Экземпляр индексирует агрегаты и выполняет их во время обработки.|  
|*LazyOptimizations*|Экземпляр индексирует агрегаты и выполняет их после обработки.|  
  
 Перечисление, соответствующее разрешенным значениям для **ProcessingMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ProcessingMode>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
