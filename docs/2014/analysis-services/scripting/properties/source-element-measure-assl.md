---
title: Исходный элемент (Measure) (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Source Element (Measure)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Source
helpviewer_keywords:
- Source element
ms.assetid: 9bae7ba4-3065-4623-b3e0-d54cebea7503
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 933851f354f14e325608c954ce77ba5f3d034a10
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117330"
---
# <a name="source-element-measure-assl"></a>Элемент Source (Measure) (ASSL)
  Содержит сведения об источнике, содержащем значение [мер](../objects/measure-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Measure>  
      ...  
   <Source xsi:type="DataItem">...</Source>  
      ...  
</Measure>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Меры](../objects/measure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 `Source` Из `DataItem`, который используется в качестве `Source` из `Measure`, в свою очередь может иметь тип [RowBinding](../data-type/binding-data-type-assl.md), [ColumnBinding](../data-type/columnbinding-data-type-assl.md), [MeasureBinding ](../data-type/measurebinding-data-type-assl.md), или [CubeDimensionBinding](../data-type/dimensionbinding-data-type-assl.md).  
  
 Дополнительные сведения о `DataItem` типа, включая таблицы объектов языка ASSL и свойства `DataItem` введите, см. в разделе [тип данных DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Элемент, соответствующий родителю параметра `Source` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
