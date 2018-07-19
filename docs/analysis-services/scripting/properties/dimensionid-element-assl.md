---
title: Элемент DimensionID (ASSL) | Документация Майкрософт
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 340225d519cb119daaae4628033e67a9f007d830
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052712"
---
# <a name="dimensionid-element-assl"></a>Элемент DimensionID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит идентификатор измерения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeDimension> <!-- or DimensionBinding, DimensionAttributeBinding -- >  
   ...  
   <DimensionID>...</DimensionID>  
      ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md), [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md), [DimensionAttributeBinding](../../../analysis-services/scripting/data-type/dimensionattributebinding-data-type-out-of-line-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элементы, соответствующие родителям элемента **DimensionID** в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.CubeDimension> и <xref:Microsoft.AnalysisServices.DimensionBinding>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
