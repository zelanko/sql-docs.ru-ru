---
title: Элемент StorageMode (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f5dbcd8ebf37bb197ccb743a6b78d009ad93e19d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="storagemode-element-assl"></a>Элемент StorageMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Родительские элементы|[Куб элемент &#40;ASSL&#41;](../../../analysis-services/scripting/objects/cube-element-assl.md), [измерения элемент &#40;ASSL&#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md), [элемент MeasureGroup &#40;ASSL&#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [секции Элемент &#40;ASSL&#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*MOLAP*|Родительский элемент использует многомерное хранилище OLAP (MOLAP).|  
|*ROLAP*|Родительский элемент использует реляционное хранилище OLAP (ROLAP).|  
|*HOLAP*|Родительский элемент использует гибридное хранилище OLAP (HOLAP).<br /><br /> Примечание: Это значение не является допустимым для [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md) от родительского элемента.|  
|*InMemory*|Родительский элемент использует хранилище IMBI.|  
  
 Перечисление, соответствующее разрешенным значениям для **StorageMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.StorageMode>.  
  
 Элементы, соответствующие родителям элемента **StorageMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup>, и <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
