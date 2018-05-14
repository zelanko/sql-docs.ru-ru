---
title: Элемент MeasureGroups (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f0fde83c43de68b648c64ea02aaa6d5e4c518822
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="measuregroups-element-assl"></a>Элемент MeasureGroups (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит коллекцию элементов [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) , связанных с родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cube> <!-- or CubeBinding, Perspective -->  
   ...  
   <MeasureGroups>  
      <MeasureGroup>...</MeasureGroup> <!-- parent: Cube -->  
      <MeasureGroup xsi:type="MeasureGroupBinding">...</MeasureGroup> <!-- parent: CubeBinding -->  
      <MeasureGroup xsi:type="PerspectiveMeasureGroup">...</MeasureGroup> <!-- parent: Perspective -->  
   </MeasureGroups>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md), [CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md), [Perspective](../../../analysis-services/scripting/objects/perspective-element-assl.md)|  
|Дочерние элементы|См. в таблице.|  
  
|Предок или родитель|Дочерний элемент|  
|------------------------|-------------------|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|[Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|[CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md)|[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) типа [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|[Перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md)|[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) типа [PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов AMO — это <xref:Microsoft.AnalysisServices.MeasureGroupCollection> или <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroupCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
