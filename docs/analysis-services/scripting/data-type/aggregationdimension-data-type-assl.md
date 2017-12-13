---
title: "Тип данных AggregationDimension (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AggregationDimension Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AggregationDimension
helpviewer_keywords: AggregationDimension data type
ms.assetid: 697e0e09-3210-4a56-882f-80726abc4c68
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cd73d9a355f19357ea22f5554d56dfe4eaaff6d6
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="aggregationdimension-data-type-assl"></a>Тип данных AggregationDimension (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет тип-примитив, представляющий связь между измерением и [статистической обработки](../../../analysis-services/scripting/objects/aggregation-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
   <Attributes>...</Attributes>  
      <Annotations>...</Annotations>  
</AggregationDimension>  
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
|Дочерние элементы|[Заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [атрибуты](../../../analysis-services/scripting/collections/attributes-element-assl.md), [CubeDimensionID](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md)|  
|Производные элементы|[Измерение](../../../analysis-services/scripting/objects/dimension-element-assl.md) ([измерения](../../../analysis-services/scripting/collections/dimensions-element-assl.md) коллекцию [статистической обработки](../../../analysis-services/scripting/objects/aggregation-element-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AggregationDimension>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
