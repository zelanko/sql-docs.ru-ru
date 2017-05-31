---
title: "Класс событий Background Job Error | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Background Job Error event class
ms.assetid: 9e6d2a0e-919d-4fe2-a306-b20b8d41c197
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bae056c3dd2b646bf7e4ec88e7c5d2e8d11bc7f8
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="background-job-error-event-class"></a>Background Job Error, класс событий
  Класс событий **Background Job Error** происходит при аварийном завершении фонового задания. Эта ситуация может потребовать вмешательства системного администратора.  
  
## <a name="background-job-error-event-class-data-columns"></a>Столбцы данных класса событий Background Job Error  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной заданием. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**DatabaseName**|**nvarchar**|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|**Ошибка**|**int**|Номер ошибки последней попытки (только**EventSubClass** 1).|31|Да|  
|**EventClass**|**int**|Тип события = 193.|27|Нет|  
|**EventSequence**|**int**|Порядковый номер данного события в запросе.|51|Нет|  
|**EventSubClass**|**int**|Тип подкласса события.<br /><br /> 1 = Выполнение фонового задания прекращено после сбоя.<br /><br /> 2 = Фоновое задание сброшено: очередь переполнена.<br /><br /> 3 = Фоновое задание возвратило ошибку.|21|Да|  
|**IndexID**|**int**|Идентификатор индекса объекта, связанного с событием. Чтобы определить идентификатор индекса для объекта, используйте столбец **indid** в системной таблице **sysindexes** .|24|Да|  
|**IntegerData**|**int**|Число попыток, предпринятых заданием (только**EventSubClass** 1).|25|Да|  
|**IntegerData2**|**int**|Последовательный номер задания.|55|Да|  
|**ObjectID**|**int**|Идентификатор объекта, назначенный системой.|22|Да|  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, создавшего сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени Имя_входа1 и при выполнении инструкции под именем Имя_входа2 **SessionLoginName** содержит значение «Имя_входа1», а **LoginName** содержит значение «Имя_входа2». В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|64|Да|  
|**Severity**|**int**|Серьезность ошибки последней попытки (только**EventSubClass** 1).|20|Да|  
|**StartTime**|**datetime**|Время создания задания.|14|Да|  
|**Состояние**|**int**|Состояние ошибки последней попытки (только**EventSubClass** 1).|30|Да|  
|**TextData**|**ntext**|Текстовое описание значения подкласса событий.|1|Да|  
|**Тип**|**int**|Тип задания.|57|Да|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Класс событий Auto Stats](../../relational-databases/event-classes/auto-stats-event-class.md)  
  
  
