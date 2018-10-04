---
title: Класс событий PreConnect:Completed | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 16720db613815d5c8cce501c1cee2d5d3cc9b3cb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150634"
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed, класс событий
  Класс событий PreConnect:Completedevent указывает на завершение триггера LOGON или функции-классификатора регулятора ресурсов.  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>Столбцы данных класса событий PreConnect:Completed  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|216|27|Нет|  
|SPID|`int`|Идентификатор процесса сервера, создающего это событие.|12|Да|  
|EventSubClass|`int`|1 для определяемой пользователем функции-классификатора.|21|Да|  
|StartTime|`datetime`|Время начала выполнения определяемой пользователем функции-классификатора.|14|Да|  
|EndTime|`datetime`|Время начала выполнения определяемой пользователем функции-классификатора.|15|Да|  
|Duration|`bigint`|Количество времени (в миллисекундах), затраченного функцией-классификатором.|13|Да|  
|ObjectID|`int`|Идентификатор определяемого пользователем объекта-классификатора.|22|Да|  
|ЦП|`int`|Использование ЦП в миллисекундах.|18|Да|  
|Reads|`int`|Количество операций логического считывания.|16|Да|  
|Writes|`int`|Количество операций логической записи.|17|Да|  
|GroupID|`int`|Идентификатор классифицированной группы рабочей нагрузки.|66|Да|  
|Ошибка|`int`|Номер последней ошибки в случае, если выполнение определяемой пользователем функции-классификатора завершилось с ошибкой.|31|Да|  
|Состояние|`int`|Состояние последней ошибки.|30|Да|  
|TargetUserName|`sysname`|Возвращаемое значение (имя группы рабочей нагрузки) для определяемой пользователем функции-классификатора, если системе не удается найти соответствующую активную группу. В противном случае этот столбец содержит значение NULL.|39|Да|  
|ObjectName|`nvarchar(256)`|Двухкомпонентное имя определяемой пользователем функции-классификатора. Например, dbo.classifier.|34|Да|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)   
 [PreConnect:Starting, класс событий](preconnect-starting-event-class.md)   
 [регулятор ресурсов](../resource-governor/resource-governor.md)  
  
  
