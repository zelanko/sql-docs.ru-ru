---
title: Элемент ReportingWeekToMonthPattern (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ReportingWeekToMonthPattern Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReportingWeekToMonthPattern
helpviewer_keywords:
- ReportingWeekToMonthPattern element
ms.assetid: 8d7c694d-d5c5-4faa-af78-155779e84fe9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 61667552266673b71bae7b8046e47d6c4db5c9f1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083424"
---
# <a name="reportingweektomonthpattern-element-assl"></a>Элемент ReportingWeekToMonthPattern (ASSL)
  Определяет шаблон соответствия отчетных недель и месяцев для [TimeBinding](../data-type/binding-data-type-assl.md) элемент.  
  
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*445*|4 недель в первом месяце квартала, 4 недели во втором месяце и 5 недель в третьем месяце.|  
|*454*|4 недель в первом месяце квартала, 5 недель, во втором месяце и 4 недели в третьем месяце.|  
|*544*|5 недель в первом месяце квартала, 4 недели во втором месяце и 4 недели в третьем месяце.|  
  
 Перечисление, соответствующее допустимым значениям элемента `ReportingWeekToMonthPattern` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.ReportingWeekToMonthPattern>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
