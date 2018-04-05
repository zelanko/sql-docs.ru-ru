---
title: Элемент IntermediateGranularityAttributeID (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IntermediateGranularityAttributeID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- IntermediateGranularityAttributeID
helpviewer_keywords:
- IntermediateGranularityAttributeID element
ms.assetid: 49895ff0-cb0d-4bcc-ab73-8cb3d5961e12
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0ab6203fa49448fc3a9059f6cedfffd33d169d86
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="intermediategranularityattributeid-element-assl"></a>Элемент IntermediateGranularityAttributeID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит идентификатор атрибута гранулярности в промежуточном измерении куба, используемый для связывает ссылочное измерение с промежуточным (ID).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ReferenceMeasureGroupDimension>  
   ...  
   <IntermediateGranularityAttributeID>...  
   </IntermediateGranularityAttributeID>  
   ...  
</ReferenceMeasureGroupDimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ReferenceMeasureGroupDimension](../../../analysis-services/scripting/data-type/referencemeasuregroupdimension-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Элемент, соответствующий родителю параметра **IntermediateGranularityAttributeID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
