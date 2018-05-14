---
title: Элемент RelationshipType (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c74d8bc597eaee5ca6842d2c9545d399a16e21f7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="relationshiptype-element-assl"></a>Элемент RelationshipType (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает, является ли связей элементов для [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md) можно изменить.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <RelationshipType>...</RelationshipType>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Гибкие*|  
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
|*Жесткая*|Связи элементов между атрибутом и связанным атрибутом не могут быть изменены.|  
|*Гибкие*|Связи элементов между атрибутом и связанным атрибутом могут быть изменены.|  
  
 Например, если для элемента **ZipCode** нельзя заменить одно значение **City** на другое, то связь между **ZipCode** и **City** помечается как *Rigid*.  
  
 Перечисление, соответствующее разрешенным значениям для **RelationshipType** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.RelationshipType>.  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и иерархии атрибутов](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
