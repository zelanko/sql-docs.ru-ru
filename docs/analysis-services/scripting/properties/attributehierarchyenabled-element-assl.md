---
title: "Элемент AttributeHierarchyEnabled (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AttributeHierarchyEnabled Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AttributeHierarchyEnabled
helpviewer_keywords:
- AttributeHierarchyEnabled element
ms.assetid: 1e95307f-530e-4e98-a0e1-2b0462d330a3
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cddc7cbc87e9644667d5012803ad52a80a572ce7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="attributehierarchyenabled-element-assl"></a>Элемент AttributeHierarchyEnabled (ASSL)
  Определяет, включена ли иерархия атрибутов для атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute><!-- or CubeAttribute -->  
   ...  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Boolean|  
|Значение по умолчанию|**True**|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **AttributeHierarchyEnabled** определяет, формируется ли иерархия атрибутов службами [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для атрибута. Если иерархия атрибута отключена, то атрибут нельзя использовать в пользовательской иерархии или нельзя ссылаться на иерархию в инструкциях многомерных выражений.  
  
 Элементы, соответствующие родителям элемента **AttributeHierarchyEnabled** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CubeAttribute> и <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент AttributeHierarchyVisible &#40; ASSL &#41;](../../../analysis-services/scripting/properties/attributehierarchyvisible-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

