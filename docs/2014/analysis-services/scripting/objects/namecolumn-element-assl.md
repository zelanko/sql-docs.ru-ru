---
title: Элемент NameColumn (ASSL) | Документы Microsoft
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
- NameColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NameColumn
helpviewer_keywords:
- NameColumn element
ms.assetid: 9ff79f2e-26d7-4ab9-a166-14c2c2d1fc07
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 41a290275de98b460d16115a2c99774bbf6ede9e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188557"
---
# <a name="namecolumn-element-assl"></a>Элемент NameColumn (ASSL)
  Идентифицирует столбец, предоставляющий имя родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <NameColumn xsi:type="DataItem">...</NameColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
|Предок или родитель|Значение по умолчанию|  
|------------------------|-------------------|  
|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|Разное (см. примечания)|  
|[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|None|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если [KeyColumns](../collections/columns-element-assl.md) коллекцию `DimensionAttribute` содержит один [KeyColumn](column-element-assl.md) элемент, представляющий ключевой столбец со строковым типом данных, то `DataItem` значения, используются значения по умолчанию `NameColumn` элемент.  
  
 Дополнительные сведения о `DataItem` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) и свойства `DataItem` введите см. в разделе [DataItem, тип данных &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Элементы, соответствующие родителям элемента `NameColumn` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DimensionAttribute> и <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также  
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  