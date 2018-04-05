---
title: Элемент ReportingWeekToMonthPattern (ASSL) | Документы Microsoft
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
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c58d5d176b50b23f6f6f26f32a9d1b8d97456dbf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="reportingweektomonthpattern-element-assl"></a>Элемент ReportingWeekToMonthPattern (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет шаблон соответствия отчетных недель и месяцев для [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<TimeBinding>  
   ...  
   <ReportingWeekToMonthPattern>...</ReportingWeekToMonthPattern>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*445*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*445*|4 недель в первом месяце квартала, 4 недели во втором месяце и 5 недель в третьем месяце.|  
|*454*|4 недель в первом месяце квартала, 5 недель, во втором месяце и 4 недели в третьем месяце.|  
|*544*|5 недель в первом месяце квартала, 4 недели во втором месяце и 4 недели в третьем месяце.|  
  
 Перечисление, соответствующее разрешенным значениям для **ReportingWeekToMonthPattern** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ReportingWeekToMonthPattern>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
