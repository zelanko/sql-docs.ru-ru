---
title: Категория событий отчеты о состоянии | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- progress events [Analysis Services]
- Progress Reports event category
- event classes [Analysis Services], progress reports
ms.assetid: c130f160-28ef-49bc-9ee6-da47dc9aab2a
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8bcfa530f87d7a8caaee6814c2e2e2282e2783ed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087455"
---
# <a name="progress-reports-event-category"></a>категория событий «Отчеты о состоянии»
  Категория событий «Отчеты о состоянии» содержит классы событий, описанные в следующей таблице.  
  
|Класс событий|Идентификатор события|Описание|  
|-----------------|--------------|-----------------|  
|Начало отчета о состоянии|5|Позволяет собрать все события начала отчета о состоянии с момента запуска трассировки.|  
|Окончание отчета о состоянии|6|Собирает все события окончания отчета о состоянии с момента запуска трассировки.|  
|Текущий отчет о состоянии|7|Собирает все текущие события отчета о состоянии с момента запуска трассировки. Например, во время обработки текущие отчеты включают в себя данные, относящиеся к обрабатываемым объектам (измерения, секции, куб и т. д.).|  
|Ошибка отчета о состоянии|8|Собирает все события ошибки отчета о состоянии с момента запуска трассировки.|  
  
 Каждое событие начала отчета о состоянии начинается с потока событий состояния и завершается событием конца отчета о состоянии. В потоке может содержаться любое количество событий ошибки отчета о состоянии и текущих событий отчета о состоянии.  
  
 Дополнительные сведения о столбцах, связанных с каждым из классов событий «Отчеты о состоянии», см. в разделе [Progress Reports Data Columns](progress-reports-data-columns.md).  
  
## <a name="see-also"></a>См. также  
 [События трассировки служб Analysis Services](analysis-services-trace-events.md)  
  
  