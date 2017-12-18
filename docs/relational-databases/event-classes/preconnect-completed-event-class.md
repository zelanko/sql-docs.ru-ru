---
title: "Класс событий PreConnect:Completed | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: event-classes
ms.reviewer: 
ms.suite: sql
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
ms.openlocfilehash: 9ba5e00939d88a810ac709c451d3d9a26706d218
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed, класс событий
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] Класс событий PreConnect:Completedevent указывает на завершение триггера LOGON или функции-классификатора Resource Governor.  
  
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
  
  
