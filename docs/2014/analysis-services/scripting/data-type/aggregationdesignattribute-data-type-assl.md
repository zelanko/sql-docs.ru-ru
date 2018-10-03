---
title: Тип данных AggregationDesignAttribute (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationDesignAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesignAttribute
helpviewer_keywords:
- AggregationDesignAttribute data type
ms.assetid: 03d29d76-e4bd-4035-92cc-35149d83fbf9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c20be714c6a302f7ba913cacc67b86f70c5379f0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163310"
---
# <a name="aggregationdesignattribute-data-type-assl"></a>Тип данных AggregationDesignAttribute (ASSL)
  Определяет тип-примитив, представляющий взаимосвязь между атрибутом и [AggregationDesignDimension](dimension-data-type-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationDesignAttribute>  
   <AttributeID>...</AttributeID>  
      <EstimatedCount>...</EstimatedCount>  
</AggregationDesignAttribute>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[AttributeID](../properties/id-element-assl.md), [EstimatedCount](../properties/estimatedcount-element-assl.md)|  
|Производные элементы|[Атрибут](../objects/attribute-element-assl.md) ([атрибуты](../collections/attributes-element-assl.md) коллекцию [AggregationDesignDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.AggregationDesignAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных AggregationDesignDimension &#40;ASSL&#41;](dimension-data-type-assl.md)   
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
