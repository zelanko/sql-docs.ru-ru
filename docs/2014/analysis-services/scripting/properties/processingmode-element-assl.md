---
title: Элемент ProcessingMode (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ProcessingMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ProcessingMode
helpviewer_keywords:
- ProcessingMode element
ms.assetid: dff6eeba-f09c-4d8c-ad81-caef76254af0
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9a966a1d800107b18316e875bd8c9552df613cfe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273790"
---
# <a name="processingmode-element-assl"></a>Элемент ProcessingMode (ASSL)
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
|Значение по умолчанию|*Регулярные*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Куб](../objects/cube-element-assl.md), [измерения](../objects/dimension-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [секции](../objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение `ProcessingMode` элемента `Cube` предоставляет значения по умолчанию для куба и может переопределяться установкой `ProcessingMode` для каждой секции.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Регулярные*|Экземпляр индексирует агрегаты и выполняет их во время обработки.|  
|*LazyOptimizations*|Экземпляр индексирует агрегаты и выполняет их после обработки.|  
  
 Перечисление, соответствующее допустимым значениям элемента `ProcessingMode` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.ProcessingMode>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
