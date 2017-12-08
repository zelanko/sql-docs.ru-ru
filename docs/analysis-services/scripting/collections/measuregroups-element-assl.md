---
title: "Элемент MeasureGroups (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
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
apiname: MeasureGroups Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: MeasureGroups
helpviewer_keywords: MeasureGroups element
ms.assetid: 80e970e9-6ea6-47a9-9e5c-d0f9b01c09c0
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: cb7398ce2568c4fee80c8ce87e3d76431566079d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="measuregroups-element-assl"></a>Элемент MeasureGroups (ASSL)
  Содержит коллекцию элементов [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) элементы, связанные с родительским элементом.  
  
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
|Родительские элементы|[Куб](../../../analysis-services/scripting/objects/cube-element-assl.md), [CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md), [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md)|  
|Дочерние элементы|См. в таблице.|  
  
|Предок или родитель|Дочерний элемент|  
|------------------------|-------------------|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|[Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|[CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md)|[Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) типа [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|[Перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md)|[Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) типа [PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в модели объектов AMO — это <xref:Microsoft.AnalysisServices.MeasureGroupCollection> или <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroupCollection>.  
  
## <a name="see-also"></a>См. также:  
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
