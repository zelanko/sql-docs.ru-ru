---
title: "Элемент EstimatedSize (ASSL) | Документы Microsoft"
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
apiname: EstimatedSize Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: EstimatedSize
helpviewer_keywords: EstimatedSize element
ms.assetid: a9c63a22-d424-4f27-a186-5372f7b0224d
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3cb162adb6d7495d17b0ac1517604f0bb27a0d96
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="estimatedsize-element-assl"></a>Элемент EstimatedSize (ASSL)
  Содержит предполагаемый, доступный только для чтения размер родительского элемента в байтах.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Database> <!-- or MeasureGroup, Partition -->  
   ...  
   <EstimatedSize>...</EstimatedSize>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Long|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[База данных](../../../analysis-services/scripting/objects/database-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [секции](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Родителям в модели объектов AMO соответствуют элементы <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.MeasureGroup> и <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
