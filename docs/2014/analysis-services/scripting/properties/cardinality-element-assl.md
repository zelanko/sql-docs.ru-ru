---
title: Элемент Cardinality (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Cardinality Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Cardinality element
ms.assetid: 60ac8a26-7c8b-4011-9b9b-a29863779428
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c75017321a0f00a3e88a74d12336768f1bfc78b3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197844"
---
# <a name="cardinality-element-assl"></a>Элемент Cardinality (ASSL)
  Указывает количество элементов связи, описываемой [AttributeRelationship](../objects/attributerelationship-element-assl.md) или [RegularMeasureGroupDimension](../data-type/dimension-data-type-assl.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributeRelationship> <!-- or RegularMeasureGroupDimension -->  
   ...  
   <Cardinality>...</Cardinality>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Многие*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[AttributeRelationship](../objects/attributerelationship-element-assl.md), [RegularMeasureGroupDimension](../data-type/dimension-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Многие*|Связь «многие к одному»|  
|*Один*|Связь «один к одному»|  
  
 Перечисление, соответствующее допустимым значениям элемента `Cardinality` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.Cardinality>.  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и иерархии атрибутов](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
