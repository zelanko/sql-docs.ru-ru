---
title: "Категория событий отчеты о состоянии | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: trace-events
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- progress events [Analysis Services]
- Progress Reports event category
- event classes [Analysis Services], progress reports
ms.assetid: c130f160-28ef-49bc-9ee6-da47dc9aab2a
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c45bcf105dcd2de68f1ba25bdafebc9cb77c295d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="progress-reports-event-category"></a>категория событий «Отчеты о состоянии»
  Категория событий «Отчеты о состоянии» содержит классы событий, описанные в следующей таблице.  
  
|Класс событий|Идентификатор события|Description|  
|-----------------|--------------|-----------------|  
|Начало отчета о состоянии|5|Позволяет собрать все события начала отчета о состоянии с момента запуска трассировки.|  
|Окончание отчета о состоянии|6|Собирает все события окончания отчета о состоянии с момента запуска трассировки.|  
|Текущий отчет о состоянии|7|Собирает все текущие события отчета о состоянии с момента запуска трассировки. Например, во время обработки текущие отчеты включают в себя данные, относящиеся к обрабатываемым объектам (измерения, секции, куб и т. д.).|  
|Ошибка отчета о состоянии|8|Собирает все события ошибки отчета о состоянии с момента запуска трассировки.|  
  
 Каждое событие начала отчета о состоянии начинается с потока событий состояния и завершается событием конца отчета о состоянии. В потоке может содержаться любое количество событий ошибки отчета о состоянии и текущих событий отчета о состоянии.  
  
 Дополнительные сведения о столбцах, связанных с каждым из классов событий «Отчеты о состоянии», см. в разделе [Progress Reports Data Columns](../../analysis-services/trace-events/progress-reports-data-columns.md).  
  
## <a name="see-also"></a>См. также  
 [События трассировки служб Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
