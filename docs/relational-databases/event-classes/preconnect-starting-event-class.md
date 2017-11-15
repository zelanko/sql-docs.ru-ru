---
title: "Класс событий PreConnect:Starting | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6113003d6939ee0df989c0ee763e438429ffdd88
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="preconnectstarting-event-class"></a>PreConnect:Starting, класс событий
  Класс событий PreConnect:Starting показывает, когда начинается выполнение триггера LOGON или функции-классификатора регулятора ресурсов.  
  
## <a name="preconnectstarting-event-class-data-columns"></a>Столбцы данных класса событий PreConnect:Starting  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|215|27|Нет|  
|SPID|**int**|Идентификатор процесса сервера, создающего это событие.|12|Да|  
|EventSubClass|**int**|1 для определяемой пользователем функции-классификатора.|21|Да|  
|StartTime|**datetime**|Время начала выполнения определяемой пользователем функции-классификатора.|14|Да|  
|ObjectID|**int**|Идентификатор определяемого пользователем объекта-классификатора.|22|Да|  
|ObjectName|**nvarchar(256)**|Двухкомпонентное имя определяемой пользователем функции-классификатора. Например, dbo.classifier.|34|Да|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)   
 [PreConnect:Completed, класс событий](../../relational-databases/event-classes/preconnect-completed-event-class.md)   
 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)  
  
  
