---
title: "Элемент CreatedTimestamp (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CreatedTimestamp Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CreatedTimestamp
helpviewer_keywords:
- CreatedTimestamp element
ms.assetid: 35f5dd33-ea82-4be3-a117-69136aa9d1a4
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e1c17436e60809006e7204ed149d128eab4c0338
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="createdtimestamp-element-assl"></a>Элемент CreatedTimestamp (ASSL)
  Содержит отметку времени только для чтения с временем создания родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Assembly> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <CreatedTimestamp>...</CreatedTimestamp>  
   ...  
</Assembly>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|DateTime|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Сборка](../../../analysis-services/scripting/objects/assembly-element-assl.md), [куба](../../../analysis-services/scripting/objects/cube-element-assl.md), [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md), [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md), [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md), [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md), [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md), [ Раздел](../../../analysis-services/scripting/objects/partition-element-assl.md), [разрешение](../../../analysis-services/scripting/data-type/permission-data-type-assl.md), [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **CreatedTimestamp** элемент содержит только для чтения **DateTime** значение, представляющее дату и время создания объекта на заданном экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Значение этого элемента не может быть пустым.  
  
 Элементы, соответствующие родителям элемента **CreatedTimestamp** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Assembly>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.DataSourceView>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MdxScript>, <xref:Microsoft.AnalysisServices.MeasureGroup>, <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningStructure>, <xref:Microsoft.AnalysisServices.Partition>, <xref:Microsoft.AnalysisServices.Permission>, и <xref:Microsoft.AnalysisServices.Perspective>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

