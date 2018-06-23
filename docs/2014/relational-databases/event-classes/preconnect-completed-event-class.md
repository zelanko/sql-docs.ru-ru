---
title: Класс событий PreConnect:Completed | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a20bd204a726391a7fab44caccdef3b1c3437944
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194030"
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
  
  