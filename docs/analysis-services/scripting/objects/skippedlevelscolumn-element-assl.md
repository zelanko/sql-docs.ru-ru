---
title: "Элемент SkippedLevelsColumn (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
apiname: SkippedLevelsColumn Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: SkippedLevelsColumn
helpviewer_keywords: SkippedLevelsColumn element
ms.assetid: 6b00a288-99c1-4735-9e6b-cd13ed4fa346
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af0de4f281a6fd6734c8ecc456b4e80c20780a93
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="skippedlevelscolumn-element-assl"></a>Элемент SkippedLevelsColumn (ASSL)
    
> [!NOTE]  
>  В данной версии Microsoft SQL Server не поддерживается. Избегайте использовать этот компонент в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.  
  
 Предоставляет подробные сведения столбца, в котором хранится количество пропущенных (пустых) уровней между каждым элементом и его родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <SkippedLevelsColumn xsi:type="DataItem">...</SkippedLevelsColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **SkippedLevelsColumn** элемент применяется только к родительским атрибутам (другими словами, значение [использование](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) элемент для **DimensionAttribute** задать родительский Чтобы *родительского*). Элемент **SkippedLevelsColumn** содержит сведения о столбце или атрибуте родительского атрибута, в котором хранится количество пропущенных уровней между каждым элементом и его родительским элементом. Это позволяет иерархиям типа «родители-потомки», основанным на родительском атрибуте, пропускать уровни между элементами. Значения в этом столбце или атрибуте должны быть неотрицательными целыми значениями. В противном случае произойдет ошибка обработки. Если элемент **SkippedLevelsColumn** не задан или не содержит значений, то глубина уровня текущего элемента будет меньше уровня родительского элемента на единицу.  
  
 Дополнительные сведения о **DataItem** типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) и свойства **DataItem** таблицы см. в разделе [DataItem, тип данных &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Элемент, соответствующий родителю параметра **SkippedLevelsColumn** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также:  
 [Атрибуты элемента &#40; ASSL &#41;](../../../analysis-services/scripting/collections/attributes-element-assl.md)   
 [Элемент измерения &#40; ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
