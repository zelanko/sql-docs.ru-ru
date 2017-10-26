---
title: "Элемент optionality (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Optionality Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Optionality element
ms.assetid: 6cd2ef0a-6fbe-4462-ab27-4cdfeb33f8ab
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8649ff45c9c6982361098d2643f7d4bc00cdf663
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="optionality-element-assl"></a>Элемент Optionality (ASSL)
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
  
|Значение|Description|  
|-----------|-----------------|  
|*Обязательное*|Каждый член связанного атрибута должен быть связан по крайней мере с одним членом атрибута, являющегося владельцем элемента **AttributeRelationship** .|  
|*Необязательно*|Каждый член связанного атрибута не обязательно должен быть связан по крайней мере с одним членом атрибута, являющегося владельцем элемента **AttributeRelationship** .|  
  
 Перечисление, соответствующее разрешенным значениям для **количества элементов** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Optionality>.  
  
## <a name="see-also"></a>См. также:  
 [Атрибуты и иерархии атрибутов](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

