---
title: Элемент DefaultMember (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DefaultMember Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultMember
helpviewer_keywords:
- DefaultMember element
ms.assetid: db4eea9f-f7cf-40de-abd0-b62014e7ec2d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6c90abe48fc1d3bfa099e39234d22df822a03782
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055304"
---
# <a name="defaultmember-element-assl"></a>Элемент DefaultMember (ASSL)
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
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[AttributePermission](../objects/attributepermission-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ManyToManyMeasureGroupDimension](../data-type/dimension-data-type-assl.md), [PerspectiveAttribute](../data-type/perspectiveattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `DefaultMember` определяет элемент по умолчанию для родительского элемента. Если `DefaultMember` не указан или имеет значение является пустой строкой, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] сами выбирают элемент для использования в качестве элемента по умолчанию.  
  
 Для элементов `ManyToManyMeasureGroupDimension` элемент `DefaultMember` содержит многомерное выражение, указывающее элемент в измерении, заданный в элементе `CubeDimensionID` для измерения `ManyToManyMeasureGroupDimension`. Многомерное выражение аналогично [StrToMember](/sql/mdx/strtomember-mdx) MDX-функцию с ключевым словом CONSTRAINED тем, что оно не может включать Многомерные или определяемые пользователем функции.  
  
 Дополнительные сведения об элементах по умолчанию см. в разделе [Определение элемента по умолчанию](../../multidimensional-models/attribute-properties-define-a-default-member.md).  
  
 Элементы, соответствующие родителям элемента `DefaultMember` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.AttributePermission>, <xref:Microsoft.AnalysisServices.DimensionAttribute> и <xref:Microsoft.AnalysisServices.PerspectiveAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
