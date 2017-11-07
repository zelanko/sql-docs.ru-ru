---
title: "Элемент RefreshPolicy (ASSL) | Документы Microsoft"
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
- RefreshPolicy Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- RefreshPolicy
helpviewer_keywords:
- RefreshPolicy element
ms.assetid: f4c36280-1a39-4f1c-a3ab-fbeb81742d6d
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 61b41604867be33a8045a80ea8bdf74cf342fba1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="refreshpolicy-element-assl"></a>Элемент RefreshPolicy (ASSL)
  Определяет, как часто в динамической части измерения или группы мер (как указано в [сохраняемости](../../../analysis-services/scripting/properties/persistence-element-assl.md) элемент) проверяется на изменения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <RefreshPolicy>...</RefreshPolicy>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|См. в следующей таблице.|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
|Предок или родитель|Значение по умолчанию|  
|------------------------|-------------------|  
|[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)|*ByQuery*|  
|[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|Нет|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*ByQuery*|Каждый запрос проверяет, не изменился ли источник данных.|  
|*ByInterval*|Источник данных проверяется только для изменения в интервале, заданном элементом [RefreshInterval](../../../analysis-services/scripting/properties/refreshinterval-element-assl.md).|  
  
 Перечисление, соответствующее разрешенным значениям для **RefreshPolicy** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.RefreshPolicy>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Persistence &#40; ASSL &#41;](../../../analysis-services/scripting/properties/persistence-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

