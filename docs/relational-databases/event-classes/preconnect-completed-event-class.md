---
title: "Класс событий PreConnect:Completed | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ce4e11d3cf710cfeafa79c9410bc40ed230f356
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed, класс событий
  Класс событий PreConnect:Completedevent указывает на завершение триггера LOGON или функции-классификатора регулятора ресурсов.  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>Столбцы данных класса событий PreConnect:Completed  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|216|27|Нет|  
|SPID|**int**|Идентификатор процесса сервера, создающего это событие.|12|Да|  
|EventSubClass|**int**|1 для определяемой пользователем функции-классификатора.|21|Да|  
|StartTime|**datetime**|Время начала выполнения определяемой пользователем функции-классификатора.|14|Да|  
|EndTime|**datetime**|Время начала выполнения определяемой пользователем функции-классификатора.|15|Да|  
|Длительность|**bigint**|Количество времени (в миллисекундах), затраченного функцией-классификатором.|13|Да|  
|ObjectID|**int**|Идентификатор определяемого пользователем объекта-классификатора.|22|Да|  
|ЦП|**int**|Использование ЦП в миллисекундах.|18|Да|  
|Reads|**int**|Количество операций логического считывания.|16|Да|  
|Writes|**int**|Количество операций логической записи.|17|Да|  
|GroupID|**int**|Идентификатор классифицированной группы рабочей нагрузки.|66|Да|  
|Ошибка|**int**|Номер последней ошибки в случае, если выполнение определяемой пользователем функции-классификатора завершилось с ошибкой.|31|Да|  
|Состояние|**int**|Состояние последней ошибки.|30|Да|  
|TargetUserName|**sysname**|Возвращаемое значение (имя группы рабочей нагрузки) для определяемой пользователем функции-классификатора, если системе не удается найти соответствующую активную группу. В противном случае этот столбец содержит значение NULL.|39|Да|  
|ObjectName|**nvarchar(256)**|Двухкомпонентное имя определяемой пользователем функции-классификатора. Например, dbo.classifier.|34|Да|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)   
 [PreConnect:Starting, класс событий](../../relational-databases/event-classes/preconnect-starting-event-class.md)   
 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)  
  
  
