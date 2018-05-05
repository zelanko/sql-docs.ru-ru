---
title: Элемент StorageMode (ASSL) | Документы Microsoft
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
manager: kfile
ms.openlocfilehash: 6742eaff827086c8aac5d39e51dbf2e296c6b15d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
