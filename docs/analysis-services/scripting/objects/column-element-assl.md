---
title: Элемент Column (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5d43447085387ddb04be6345a762702297f3ffe2
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="column-element-assl"></a>Элемент Column (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Описывает столбец в коллекции столбцов, связанной с родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Columns>  
   <Column xsi:type="MeasureBinding">...</Column> <!-- parent of collection: DrillThroughAction -->  
   <!-- or -->  
   <Column xsi:type="CubeAttributeBinding">...</Column> <!-- parent of collection: DrillThroughAction -->  
   <!-- or -->  
   <Column xsi:type="EventColumn">...</Column> <!-- parent of collection: Event -->  
   <!-- or -->  
   <Column xsi:type="MiningModelColumn">...</Column> <!-- parent of collection: MiningModel or MiningModelColumn -->  
   <!-- or -->  
   <Column xsi:type="MiningStructureColumn">...</Column> <!-- parent of collection: MiningStructure or TableMiningStructureColumn -->  
</Columns>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
 **Тип данных и длина**  
  
|Предок или родитель|Тип данных|  
|------------------------|---------------|  
|[DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)|[MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md), [CubeAttributeBinding](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md)|  
|[Событие](../../../analysis-services/scripting/objects/event-element-assl.md)|[EventColumn](../../../analysis-services/scripting/data-type/eventcolumn-data-type-assl.md)|  
|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)|[MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)|  
|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md), [TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)|  
  
 **Значение по умолчанию**: нет  
  
 **Количество элементов**  
  
|Предок или родитель|Количество элементов|  
|------------------------|-----------------|  
|[Событие](../../../analysis-services/scripting/objects/event-element-assl.md)|1-N: обязательный элемент, который может встречаться несколько раз.|  
|Все остальные|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Столбцы](../../../analysis-services/scripting/collections/columns-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="see-also"></a>См. также:  
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
