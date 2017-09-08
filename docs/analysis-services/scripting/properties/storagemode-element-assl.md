---
title: "Элемент StorageMode (ASSL) | Документы Microsoft"
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
- StorageMode Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- StorageMode
helpviewer_keywords:
- StorageMode element
ms.assetid: 197e8153-1ab6-43ba-a7e9-ae9be19ac511
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd6ed7838025255015c3a4103689b772dd035771
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="storagemode-element-assl"></a>Элемент StorageMode (ASSL)
  Определяет режим хранения для родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <StorageMode>...</StorageMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*MOLAP*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Элемент CUBE &#40; ASSL &#41; ](../../../analysis-services/scripting/objects/cube-element-assl.md), [Измерения элемент &#40; ASSL &#41; ](../../../analysis-services/scripting/objects/dimension-element-assl.md), [Элемент MeasureGroup &#40; ASSL &#41; ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [Секции элемент &#40; ASSL &#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*MOLAP*|Родительский элемент использует многомерное хранилище OLAP (MOLAP).|  
|*ROLAP*|Родительский элемент использует реляционное хранилище OLAP (ROLAP).|  
|*HOLAP*|Родительский элемент использует гибридное хранилище OLAP (HOLAP).<br /><br /> Примечание: Это значение не является допустимым для [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md) от родительского элемента.|  
|*InMemory*|Родительский элемент использует хранилище IMBI.|  
  
 Перечисление, соответствующее разрешенным значениям для **StorageMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.StorageMode>.  
  
 Элементы, соответствующие родителям элемента **StorageMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup>, и <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
