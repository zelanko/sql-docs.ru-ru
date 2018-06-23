---
title: Тип данных AggregationDesignAttribute (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a6d65f5cbd6173218b4d33448ec442002290aad6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195258"
---
# <a name="aggregationdesignattribute-data-type-assl"></a>Тип данных AggregationDesignAttribute (ASSL)
  Определяет тип-примитив, представляющий взаимосвязь между атрибутом и [AggregationDesignDimension](dimension-data-type-assl.md) элемента.  
  
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
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AggregationDesignAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных AggregationDesignDimension &#40;ASSL&#41;](dimension-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  