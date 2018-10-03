---
title: Элемент ValueColumn (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ValueColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ValueColumn element
ms.assetid: 6c2d6822-8ecc-46df-9fa9-bb92ac716c36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 876d5efb4d4b84e8f42cfd3c360258c8cb67d865
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048145"
---
# <a name="valuecolumn-element-assl"></a>Элемент ValueColumn (ASSL)
  Определяет столбец, предоставляющий значение родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <ValueColumn xsi:type="DataItem">...</ValueColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Значение по умолчанию|Разное (см. примечания)|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если [NameColumn](namecolumn-element-assl.md) элемент `DimensionAttribute` указано, же `DataItem` значение используется в качестве значения по умолчанию для `ValueColumn` элемент. Если `NameColumn` элемент `DimensionAttribute` не указан и [KeyColumns](../collections/keycolumns-element-assl.md) коллекцию `DimensionAttribute` содержит один [KeyColumn](keycolumn-element-assl.md) элемент, представляющий ключевой столбец со строкой типом данных, то `DataItem` значение используется в качестве значения по умолчанию для `ValueColumn` элемент.  
  
 Дополнительные сведения о `DataItem` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) и свойства `DataItem` введите, см. в разделе [тип данных DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Элементы, соответствующие родителям элемента `NameColumn` в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.DimensionAttribute> и <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также  
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
