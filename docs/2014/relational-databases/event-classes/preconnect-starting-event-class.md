---
title: Класс событий PreConnect:Starting | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0986e654430a47cc494bf1646c222b4888fc105b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63033516"
---
# <a name="preconnectstarting-event-class"></a>PreConnect:Starting, класс событий
  Класс событий PreConnect:Starting показывает, когда начинается выполнение триггера LOGON или функции-классификатора регулятора ресурсов.  
  
## <a name="preconnectstarting-event-class-data-columns"></a>Столбцы данных класса событий PreConnect:Starting  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|215|27|Нет|  
|SPID|`int`|Идентификатор процесса сервера, создающего это событие.|12|Да|  
|EventSubClass|`int`|1 для определяемой пользователем функции-классификатора.|21|Да|  
|StartTime|`datetime`|Время начала выполнения определяемой пользователем функции-классификатора.|14|Да|  
|ObjectID|`int`|Идентификатор определяемого пользователем объекта-классификатора.|22|Да|  
|ObjectName|`nvarchar(256)`|Двухкомпонентное имя определяемой пользователем функции-классификатора. Например, dbo.classifier.|34|Да|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)   
 [PreConnect:Completed, класс событий](preconnect-completed-event-class.md)   
 [регулятор ресурсов](../resource-governor/resource-governor.md)  
  
  
