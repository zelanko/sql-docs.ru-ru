---
title: "Элемент LogFileSize (ASSL) | Документы Microsoft"
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
apiname: LogFileSize Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: LogFileSize
helpviewer_keywords: LogFileSize element
ms.assetid: d2135e68-57a9-4144-8403-9627041f2a58
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 09b2f3d2f613082947abf04633cc83f65a6817e3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="logfilesize-element-assl"></a>Элемент LogFileSize (ASSL)
  Определяет максимальный размер файла журнала в мегабайтах.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Trace>  
  
   <LogFileSize>...</LogFileSize>  
  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|**5** (мегабайт)|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **LogFileSize** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент traces &#40; ASSL &#41;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
