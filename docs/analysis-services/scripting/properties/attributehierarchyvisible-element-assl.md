---
title: Элемент AttributeHierarchyVisible (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 81762d27a57b4c4d2aa4c9bed829059cc3664c0c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="attributehierarchyvisible-element-assl"></a>Элемент AttributeHierarchyVisible (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет, является ли иерархия атрибутов видимой для клиентских приложений.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute> <!-- or CubeAttribute or PerspectiveAttribute -->  
   ...  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
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
|Родительский элемент|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [PerspectiveAttribute](../../../analysis-services/scripting/data-type/perspectiveattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент **AttributeHierarchyVisible** определяет, видима ли для клиентских приложений иерархия атрибута, связанная с атрибутом. Если этот элемент имеет значение **False**, иерархию атрибута все равно можно использовать для создания определяемых пользователем иерархий и на нее можно ссылаться в инструкциях многомерных выражений.  
  
 Элементы, соответствующие родителям элемента **AttributeHierarchyVisible** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CubeAttribute>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, и <xref:Microsoft.AnalysisServices.PerspectiveAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Элемент AttributeHierarchyEnabled &#40;ASSL&#41;](../../../analysis-services/scripting/properties/attributehierarchyenabled-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
