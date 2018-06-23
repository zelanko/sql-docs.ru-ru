---
title: Элемент CustomRollupPropertiesColumn (ASSL) | Документы Microsoft
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
- CustomRollupPropertiesColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CustomRollupPropertiesColumn
helpviewer_keywords:
- CustomRollupPropertiesColumn element
ms.assetid: 7f4a9825-c768-4523-acb3-511a5160fd44
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c9452dbc1d6c3104fe76760ad4460e636fdd45fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101152"
---
# <a name="customrolluppropertiescolumn-element-assl"></a>Элемент CustomRollupPropertiesColumn (ASSL)
  Определяет подробные сведения столбца, содержащего свойства формулы пользовательской свертки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <CustomRollupPropertiesColumn xsi:type="DataItem">...</CustomRollupPropertiesColumn>  
   ...  
</DimensionAttribute>  
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
|Родительские элементы|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о `DataItem` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) и свойства `DataItem` введите см. в разделе [DataItem, тип данных &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Элемент, соответствующий родителю параметра `CustomRollupPropertiesColumn` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CustomRollupColumn &#40;ASSL&#41;](column-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  