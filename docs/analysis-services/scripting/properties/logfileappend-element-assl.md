---
title: "Элемент LogFileAppend (ASSL) | Документы Microsoft"
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
apiname: LogFileAppend Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: LogFileAppend
helpviewer_keywords: LogFileAppend element
ms.assetid: f85e94a9-e5c5-478a-a5a0-fc99ed19b582
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a6af2ce43451db0ed1c0eee88c6248d8487639aa
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="logfileappend-element-assl"></a>Элемент LogFileAppend (ASSL)
  Определяет, является ли [трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md) элемент присоединять свой выход ведения журнала к существующему файлу журнала или перезаписывать его.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Trace>  
  
   <LogFileAppend>...</LogFileAppend>  
  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Boolean|  
|Значение по умолчанию|False|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **LogFileAppend** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент traces &#40; ASSL &#41;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
