---
title: Тип данных AggregationAttribute (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f70849c878feb95eab4e55b41ce7a203721ab294
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="aggregationattribute-data-type-assl"></a>Тип данных AggregationAttribute (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет примитивный тип данных, представляющий взаимосвязь между элементом [Aggregation](../../../analysis-services/scripting/objects/aggregation-element-assl.md) и атрибутом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationAttribute>  
   <AttributeID>...</AttributeID>  
      <Annotations>...</Annotations>  
</AggregationAttribute>  
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
|Дочерние элементы|[AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
|Производные элементы|[Attribute](../../../analysis-services/scripting/objects/attribute-element-assl.md) (коллекция[Attributes](../../../analysis-services/scripting/collections/attributes-element-assl.md) элементов [AggregationDimension](../../../analysis-services/scripting/data-type/aggregationdimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Соответствующим классом в модели объектов AMO является <xref:Microsoft.AnalysisServices.AggregationAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Aggregation & #40; ASSL & #41;](../../../analysis-services/scripting/objects/aggregation-element-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
