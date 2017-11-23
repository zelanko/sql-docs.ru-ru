---
title: "Элемент RelationshipType (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
apiname: RelationshipType Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: RelationshipType
helpviewer_keywords: RelationshipType element
ms.assetid: 72e1ab0e-a95d-4ebe-857d-21de1bf9fe03
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6d93ac8d20a63e5815d388652e35e6d606502492
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="relationshiptype-element-assl"></a>Элемент RelationshipType (ASSL)
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
  
|Значение|Description|  
|-----------|-----------------|  
|*Жесткая*|Связи элементов между атрибутом и связанным атрибутом не могут быть изменены.|  
|*Гибкие*|Связи элементов между атрибутом и связанным атрибутом могут быть изменены.|  
  
 Например, если для элемента **ZipCode** нельзя заменить одно значение **City** на другое, то связь между **ZipCode** и **City** помечается как *Rigid*.  
  
 Перечисление, соответствующее разрешенным значениям для **RelationshipType** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.RelationshipType>.  
  
## <a name="see-also"></a>См. также:  
 [Атрибуты и иерархии атрибутов](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
