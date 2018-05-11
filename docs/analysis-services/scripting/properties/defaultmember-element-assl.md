---
title: Элемент DefaultMember (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d050c0cb2209c855da35a7f1afd2fe028575edf7
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="defaultmember-element-assl"></a>Элемент DefaultMember (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит многомерное выражение (MDX), определяющее элемент по умолчанию для родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributePermission> <!-- or DimensionAttribute, ManyToManyMeasureGroupDimension, PerspectiveAttribute -->  
      ...  
   <DefaultMember>...</DefaultMember>  
      ...  
</AttributePermission>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[AttributePermission](../../../analysis-services/scripting/objects/attributepermission-element-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [ManyToManyMeasureGroupDimension](../../../analysis-services/scripting/data-type/manytomanymeasuregroupdimension-data-type-assl.md), [PerspectiveAttribute](../../../analysis-services/scripting/data-type/perspectiveattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент **DefaultMember** определяет элемент по умолчанию для родительского элемента. Если **DefaultMember** не указан или равен пустой строке, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] сами выбирают элемент для использования в качестве элемента по умолчанию.  
  
 Для элементов **ManyToManyMeasureGroupDimension** элемент **DefaultMember** содержит многомерное выражение, указывающее элемент в измерении, заданный в элементе **CubeDimensionID** для измерения **ManyToManyMeasureGroupDimension**. Многомерное выражение аналогично [StrToMember](../../../mdx/strtomember-mdx.md) MDX-функцию с ключевым словом CONSTRAINED тем, что оно не может включать многомерных Выражений или определяемые пользователем функции.  
  
 Дополнительные сведения об элементах по умолчанию см. в разделе [Определение элемента по умолчанию](../../../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md).  
  
 Элементы, соответствующие родителям элемента **DefaultMember** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AttributePermission>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, и <xref:Microsoft.AnalysisServices.PerspectiveAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
