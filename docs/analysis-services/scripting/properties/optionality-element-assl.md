---
title: Элемент optionality (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 779a2e7f83cdd5c49d7a723c31d67224d987670f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="optionality-element-assl"></a>Элемент Optionality (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает на необязательность вложенных элементов для [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <Optionality>...</OPtionality>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Обязательное*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Обязательное*|Каждый член связанного атрибута должен быть связан по крайней мере с одним членом атрибута, являющегося владельцем элемента **AttributeRelationship** .|  
|*Необязательно*|Каждый член связанного атрибута не обязательно должен быть связан по крайней мере с одним членом атрибута, являющегося владельцем элемента **AttributeRelationship** .|  
  
 Перечисление, соответствующее разрешенным значениям для **количества элементов** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Optionality>.  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и иерархии атрибутов](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
