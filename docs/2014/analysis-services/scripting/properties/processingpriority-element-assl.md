---
title: Элемент ProcessingPriority (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ProcessingPriority Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProcessingPriority element
ms.assetid: 95d07f1c-ef8d-4e38-9682-ebb7719dbe52
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 68a37c316cee72697cc24d23152b2b7035ea2386
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121554"
---
# <a name="processingpriority-element-assl"></a>Элемент ProcessingPriority (ASSL)
  Определяет приоритет обработки для родительского объекта во время работы в фоновом режиме (например: отложенная статистическая обработка, индексирование или кластеризация).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension> <!-- or MeasureGroup, Partition -->  
   ...  
   <ProcessingPriority>...</ProcessingPriority>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|`0`|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Измерение](../data-type/dimension-data-type-assl.md), [MeasureGroup](../objects/group-element-assl.md), [секции](../objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элементы, соответствующие родителям элемента `ProcessingPriority` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup> и <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
