---
title: Элемент DefaultMember (ASSL) | Документация Майкрософт
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
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fd074ab38264bf45ad70a96c37a22bc3c3185d4a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229684"
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
  
  
