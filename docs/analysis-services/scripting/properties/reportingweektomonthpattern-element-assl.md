---
title: Элемент ReportingWeekToMonthPattern (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: aebaad3237366bd129d09c215b04ac8e8d4e2f84
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="reportingweektomonthpattern-element-assl"></a>Элемент ReportingWeekToMonthPattern (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Значение|Описание|  
|-----------|-----------------|  
|*445*|4 недель в первом месяце квартала, 4 недели во втором месяце и 5 недель в третьем месяце.|  
|*454*|4 недель в первом месяце квартала, 5 недель, во втором месяце и 4 недели в третьем месяце.|  
|*544*|5 недель в первом месяце квартала, 4 недели во втором месяце и 4 недели в третьем месяце.|  
  
 Перечисление, соответствующее разрешенным значениям для **ReportingWeekToMonthPattern** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ReportingWeekToMonthPattern>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
