---
title: Категория событий блокировки | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 46148326b3351340a57a26d445a225cbbea35220
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/08/2018
---
# <a name="lock-events-category"></a>Категория событий Lock
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Категория событий «События блокировки» содержит классы событий, описанные в следующей таблице.  
  
|Класс событий|Идентификатор события|Description|  
|-----------------|--------------|-----------------|  
|Взаимоблокировка|50|Позволяет собрать все события взаимоблокировки метаданных с момента запуска трассировки.|  
|Время ожидания блокировки|51|Позволяет собрать все события времени ожидания блокировки метаданных с момента запуска трассировки.|  
|Блокировка получена|52|Собирает сведения о блокировках, полученных с момента запуска трассировки.|  
|Блокировка снята|53|Собирает сведения о блокировках, снятых с момента запуска трассировки.|  
|Ожидание блокировки|54|Собирает сведения о блокировках в состоянии ожидания с момента запуска трассировки.|  
  
 Дополнительные сведения о столбцах, связанных с каждым из классов событий «Блокировка», см. в разделе [Lock Events Data Columns](../../analysis-services/trace-events/lock-events-data-columns.md).  
  
## <a name="see-also"></a>См. также  
 [События трассировки служб Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
