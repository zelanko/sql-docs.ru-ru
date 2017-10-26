---
title: "Элемент ReportingWeekToMonthPattern (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ReportingWeekToMonthPattern Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ReportingWeekToMonthPattern
helpviewer_keywords:
- ReportingWeekToMonthPattern element
ms.assetid: 8d7c694d-d5c5-4faa-af78-155779e84fe9
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6ae09f2dfb0917a349f4ca3688972e0d3388d040
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="reportingweektomonthpattern-element-assl"></a>Элемент ReportingWeekToMonthPattern (ASSL)
  Определяет шаблон соответствия отчетных недель и месяцев для [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<TimeBinding>  
   ...  
   <ReportingWeekToMonthPattern>...</ReportingWeekToMonthPattern>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*445*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*445*|4 недель в первом месяце квартала, 4 недели во втором месяце и 5 недель в третьем месяце.|  
|*454*|4 недель в первом месяце квартала, 5 недель, во втором месяце и 4 недели в третьем месяце.|  
|*544*|5 недель в первом месяце квартала, 4 недели во втором месяце и 4 недели в третьем месяце.|  
  
 Перечисление, соответствующее разрешенным значениям для **ReportingWeekToMonthPattern** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ReportingWeekToMonthPattern>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

