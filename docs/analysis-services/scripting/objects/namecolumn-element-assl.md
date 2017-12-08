---
title: "Элемент NameColumn (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: NameColumn Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: NameColumn
helpviewer_keywords: NameColumn element
ms.assetid: 9ff79f2e-26d7-4ab9-a166-14c2c2d1fc07
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 513b6954b19130dfe67ffdb960f3d63dbe552dbb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
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
|Тип данных и длина|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Значение по умолчанию|См. в следующей таблице.|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
|Предок или родитель|Значение по умолчанию|  
|------------------------|-------------------|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|Разное (см. примечания)|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|Нет|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Если [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md) коллекцию **DimensionAttribute** содержит один [KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md) элемент, представляющий ключевой столбец со строковым типом данных, то **DataItem** значения, используются значения по умолчанию для **NameColumn** элемента.  
  
 Дополнительные сведения о **DataItem** типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) и свойства **DataItem** введите см. в разделе [DataItem, тип данных &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Элементы, соответствующие родителям элемента **NameColumn** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DimensionAttribute> и <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также:  
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
