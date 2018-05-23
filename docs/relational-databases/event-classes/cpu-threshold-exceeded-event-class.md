---
title: Класс событий CPU Threshold Exceeded | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4f8bfbc8445aeba0ce0e280a4a2587ee3eb46c08
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="cpu-threshold-exceeded-event-class"></a>класс событий CPU Threshold Exceeded
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Класс событий CPU Threshold Exceeded указывает, что регулятор ресурсов обнаружил запрос, превышающий пороговое значение ЦП, заданное параметром REQUEST_MAX_CPU_TIME_SEC.  
  
> [!NOTE]  
>  Интервал обнаружения для этого события — пять секунд. Это событие гарантированно создается в том случае, если запрос превышает указанное ограничение в течение более чем пяти секунд. Однако, если запрос превышает указанное пороговое значение в течение меньшего времени, его обнаружение может быть пропущено в зависимости от времени поступления запроса и времени последнего прохода.  
  
## <a name="cpu-threshold-exceeded-data-columns"></a>Столбцы данных класса событий CPU Threshold Exceeded  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ЦП|**int**|Использование ЦП в миллисекундах.|18|Да|  
|EventClass|**int**|214|27|нет|  
|EventSubClass|**int**|Нарушение ограничения ЦП.|21|Да|  
|GroupID|**int**|Идентификатор группы, в которой произошло нарушение.|66|Да|  
|OwnerID|**int**|Идентификатор SPID процесса, который вызвал нарушение.|58|Да|  
|SPID|**int**|Идентификатор процесса сервера, запустившего данное событие.<br /><br /> Примечание. Он может отличаться от действительного пользовательского идентификатора SPID, если в потоке операционной системы проверка использования ЦП является фоновой задачей.|12|Да|  
|StartTime|**datetime**|Время срабатывания события.|14|Да|  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
