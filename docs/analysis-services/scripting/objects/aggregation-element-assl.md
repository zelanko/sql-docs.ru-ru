---
title: Элемент Aggregation (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eda60a7a1261c8fb97869a817a60b45f0622c131
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="aggregation-element-assl"></a>Элемент Aggregation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет один агрегат для [секции](../../../analysis-services/scripting/objects/partition-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Aggregations>  
      <Aggregation>  
      <ID>...</ID>  
      <Name>...</Name>  
      <Dimensions>...</Dimensions>  
            <Annotations>...</Annotations>  
      <Description>...</Description>  
   </Aggregation>  
</Aggregations>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Статистические выражения](../../../analysis-services/scripting/collections/aggregations-element-assl.md)|  
|Дочерние элементы|[Заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [описание](../../../analysis-services/scripting/properties/description-element-assl.md), [измерения](../../../analysis-services/scripting/collections/dimensions-element-assl.md), [идентификатор](../../../analysis-services/scripting/properties/id-element-assl.md), [имя](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Aggregation>.  
  
## <a name="see-also"></a>См. также  
 [Секции элемент &#40;ASSL&#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)   
 [Элемент AggregationDesign & #40; ASSL & #41;](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)   
 [Элемент MeasureGroup &#40;ASSL&#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)   
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
