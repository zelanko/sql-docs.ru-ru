---
title: Элемент EstimatedPerformanceGain (ASSL) | Документы Microsoft
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
- EstimatedPerformanceGain Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- EstimatedPerformanceGain
helpviewer_keywords:
- EstimatedPerformanceGain element
ms.assetid: d7487977-73c3-4244-ad5d-3c357b219db4
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e8d278e662374f6d60256b78db13de589b34b331
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="estimatedperformancegain-element-assl"></a>Элемент EstimatedPerformanceGain (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит только для чтения процент ожидаемого прироста производительности для секции.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AggregationDesign>  
      ...  
   <EstimatedPerformanceGain>...</EstimatedPerformanceGain>  
   ...  
</AggregationDesign>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Элемент, соответствующий родительский **EstimatedPerformanceGain** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AggregationDesign>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
