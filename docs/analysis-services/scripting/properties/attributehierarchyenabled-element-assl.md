---
title: Элемент AttributeHierarchyEnabled (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8f5b6c9afdba0367685ee9aee0d036bb659103b3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="attributehierarchyenabled-element-assl"></a>Элемент AttributeHierarchyEnabled (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет, включена ли иерархия атрибута для атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute><!-- or CubeAttribute -->  
   ...  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|Логическое значение|  
|Значение по умолчанию|**True**|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 **AttributeHierarchyEnabled** определяет, формируется ли иерархия атрибутов службами [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для атрибута. Если иерархия атрибута отключена, то атрибут нельзя использовать в пользовательской иерархии или нельзя ссылаться на иерархию в инструкциях многомерных выражений.  
  
 Элементы, соответствующие родителям элемента **AttributeHierarchyEnabled** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CubeAttribute> и <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент AttributeHierarchyVisible &#40; ASSL &#41;](../../../analysis-services/scripting/properties/attributehierarchyvisible-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
