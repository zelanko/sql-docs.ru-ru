---
description: PreConnect:Completed, класс событий
title: Класс событий PreConnect:Completed | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3359d9fe2b70bcc92c1ee550effc6cddbe8f184f
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97467835"
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed, класс событий
[!INCLUDE [SQL Server - ASDB](../../includes/applies-to-version/sql-asdb.md)]
  Класс событий PreConnect:Completedevent указывает на завершение триггера LOGON или функции-классификатора регулятора ресурсов.  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>Столбцы данных класса событий PreConnect:Completed  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|216|27|Нет|  
|SPID|**int**|Идентификатор процесса сервера, создающего это событие.|12|Да|  
|EventSubClass|**int**|1 для определяемой пользователем функции-классификатора.|21|Да|  
|StartTime|**datetime**|Время начала выполнения определяемой пользователем функции-классификатора.|14|Да|  
|EndTime|**datetime**|Время начала выполнения определяемой пользователем функции-классификатора.|15|Да|  
|Duration|**bigint**|Количество времени (в миллисекундах), затраченного функцией-классификатором.|13|Да|  
|ObjectID|**int**|Идентификатор определяемого пользователем объекта-классификатора.|22|Да|  
|ЦП|**int**|Использование ЦП в миллисекундах.|18|Да|  
|Операции чтения|**int**|Количество операций логического считывания.|16|Да|  
|Запись|**int**|Количество операций логической записи.|17|Да|  
|GroupID|**int**|Идентификатор классифицированной группы рабочей нагрузки.|66|Да|  
|Error|**int**|Номер последней ошибки в случае, если выполнение определяемой пользователем функции-классификатора завершилось с ошибкой.|31|Да|  
|Состояние|**int**|Состояние последней ошибки.|30|Да|  
|TargetUserName|**sysname**|Возвращаемое значение (имя группы рабочей нагрузки) для определяемой пользователем функции-классификатора, если системе не удается найти соответствующую активную группу. В противном случае этот столбец содержит значение NULL.|39|Да|  
|ObjectName|**nvarchar(256)**|Двухкомпонентное имя определяемой пользователем функции-классификатора. Например, dbo.classifier.|34|Да|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)   
 [PreConnect:Starting, класс событий](../../relational-databases/event-classes/preconnect-starting-event-class.md)   
 [Регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)  
  
  
