---
title: "Элемент DefaultMember (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
apiname: DefaultMember Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DefaultMember
helpviewer_keywords: DefaultMember element
ms.assetid: db4eea9f-f7cf-40de-abd0-b62014e7ec2d
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7ae17ef173b78ffecedb4efc01e3de4c75958c05
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
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
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[AttributePermission](../../../analysis-services/scripting/objects/attributepermission-element-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [ManyToManyMeasureGroupDimension](../../../analysis-services/scripting/data-type/manytomanymeasuregroupdimension-data-type-assl.md), [PerspectiveAttribute](../../../analysis-services/scripting/data-type/perspectiveattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент **DefaultMember** определяет элемент по умолчанию для родительского элемента. Если **DefaultMember** не указан или равен пустой строке, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] сами выбирают элемент для использования в качестве элемента по умолчанию.  
  
 Для элементов **ManyToManyMeasureGroupDimension** элемент **DefaultMember** содержит многомерное выражение, указывающее элемент в измерении, заданный в элементе **CubeDimensionID** для измерения **ManyToManyMeasureGroupDimension**. Многомерное выражение аналогично [StrToMember](../../../mdx/strtomember-mdx.md) MDX-функцию с ключевым словом CONSTRAINED тем, что оно не может включать многомерных Выражений или определяемые пользователем функции.  
  
 Дополнительные сведения об элементах по умолчанию см. в разделе [Определение элемента по умолчанию](../../../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md).  
  
 Элементы, соответствующие родителям элемента **DefaultMember** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AttributePermission>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, и <xref:Microsoft.AnalysisServices.PerspectiveAttribute>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
