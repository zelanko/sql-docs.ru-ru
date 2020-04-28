---
title: Класс событий CPU Threshold Exceeded | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cc8252d0049953f0958ea331015aae51fd737709
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62663487"
---
# <a name="cpu-threshold-exceeded-event-class"></a>класс событий CPU Threshold Exceeded
  Класс событий CPU Threshold Exceeded указывает, что регулятор ресурсов обнаружил запрос, превышающий пороговое значение ЦП, заданное параметром REQUEST_MAX_CPU_TIME_SEC.  
  
> [!NOTE]  
>  Интервал обнаружения для этого события — пять секунд. Это событие гарантированно создается в том случае, если запрос превышает указанное ограничение в течение более чем пяти секунд. Однако, если запрос превышает указанное пороговое значение в течение меньшего времени, его обнаружение может быть пропущено в зависимости от времени поступления запроса и времени последнего прохода.  
  
## <a name="cpu-threshold-exceeded-data-columns"></a>Столбцы данных класса событий CPU Threshold Exceeded  
  
|Имя столбца данных|Тип данных|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ЦП|`int`|Использование ЦП в миллисекундах.|18|Да|  
|EventClass|`int`|214|27|нет|  
|EventSubClass|`int`|Нарушение ограничения ЦП.|21|Да|  
|GroupID|`int`|Идентификатор группы, в которой произошло нарушение.|66|Да|  
|OwnerID|`int`|Идентификатор SPID процесса, который вызвал нарушение.|58|Да|  
|SPID|`int`|Идентификатор процесса сервера, запустившего данное событие.<br /><br /> Примечание. Он может отличаться от действительного пользовательского идентификатора SPID, если в потоке операционной системы проверка использования ЦП является фоновой задачей.|12|Да|  
|StartTime|`datetime`|Время срабатывания события.|14|Да|  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
