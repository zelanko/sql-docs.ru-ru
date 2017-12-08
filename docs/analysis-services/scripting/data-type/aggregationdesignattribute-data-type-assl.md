---
title: "Тип данных AggregationDesignAttribute (ASSL) | Документы Microsoft"
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
apiname: AggregationDesignAttribute Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AggregationDesignAttribute
helpviewer_keywords: AggregationDesignAttribute data type
ms.assetid: 03d29d76-e4bd-4035-92cc-35149d83fbf9
caps.latest.revision: "42"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9f293d4727a54faf7176e3fea72921dc34aab1cc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="aggregationdesignattribute-data-type-assl"></a>Тип данных AggregationDesignAttribute (ASSL)
  Определяет тип-примитив, представляющий взаимосвязь между атрибутом и [AggregationDesignDimension](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md) элемента.  
  
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
|Дочерние элементы|[AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md), [EstimatedCount](../../../analysis-services/scripting/properties/estimatedcount-element-assl.md)|  
|Производные элементы|[Атрибут](../../../analysis-services/scripting/objects/attribute-element-assl.md) ([атрибуты](../../../analysis-services/scripting/collections/attributes-element-assl.md) коллекцию [AggregationDesignDimension](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AggregationDesignAttribute>.  
  
## <a name="see-also"></a>См. также:  
 [Тип данных AggregationDesignDimension &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
