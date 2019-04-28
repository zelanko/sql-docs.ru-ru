---
title: Класс событий Blocked Process Report | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Blocked Process Report event class
ms.assetid: e8acb408-938d-4b36-81dd-04f087410cc5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5c3061794a565c4397bbf949211774306c9acebf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62664270"
---
# <a name="blocked-process-report-event-class"></a>Blocked Process Report, класс событий
  Класс событий **Blocked Process Report** показывает, что задача была заблокирована на период времени больше указанного. К данному классу событий не относятся системные задачи или задачи, ожидающие ресурсов, для которых взаимоблокировку обнаружить нельзя.  
  
 Пороговое значение и частота создания отчетов в параметре **blocked process threshold** настраиваются с помощью хранимой процедуры **sp_configure** ; значение параметра может задаваться в секундах. По умолчанию отчеты о заблокированных процессах не создаются. Дополнительные сведения о настройке параметра **blocked process threshold** см. в разделе [Параметр конфигурации сервера "blocked process threshold"](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md).  
  
 Дополнительные сведения о фильтрации данных, возвращаемых классом событий **Blocked Process Report**, см. в разделах [Фильтрация событий в трассировке (SQL Server Profiler)](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md), [Создание фильтра трассировки (Transact-SQL)](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md) и [sp_trace_setfilter (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql).  
  
## <a name="blocked-process-report-event-class-data-columns"></a>Столбцы класса событий Blocked Process Report  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|Идентификатор базы данных, в которой запрашивается блокировка. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**Длительность**|**bigint**|Время (в миллисекундах), в течение которого процесс был заблокирован.|13|Да|  
|**EndTime**|**datetime**|Время окончания события. Этот столбец не заполняется для классов событий запуска, таких как **SQL:BatchStarting** или **SP:Starting**.|15|Да|  
|**EventClass**|**int**|Тип события = 137.|27|Нет|  
|**EventSequence**|**int**|Порядковый номер данного события в запросе.|51|Нет|  
|**IndexID**|**int**|Идентификатор индекса объекта, связанного с событием. Чтобы определить идентификатор индекса для объекта, используйте столбец **indid** в системной таблице **sysindexes** .|24|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Системный поток всегда передает отчет об этом событии. IsSystem = 1; SID = sa.|41|Да|  
|**Режим**|**int**|Состояние, которое получило или запрашивает событие.<br /><br /> 0 = NULL<br /><br /> 1 = Sch-S<br /><br /> 2 = Sch-M<br /><br /> 3=S<br /><br /> 4=U<br /><br /> 5=X<br /><br /> 6=IS<br /><br /> 7=IU<br /><br /> 8=IX<br /><br /> 9=SIU<br /><br /> 10=SIX<br /><br /> 11=UIX<br /><br /> 12=BU<br /><br /> 13=RangeS-S<br /><br /> 14=RangeS-U<br /><br /> 15=RangeI-N<br /><br /> 16=RangeI-S<br /><br /> 17 = RangeI-U<br /><br /> 18 = RangeI-X<br /><br /> 19 = RangeX-S<br /><br /> 20 = RangeX-U<br /><br /> 21 = RangeX-X|32|Да|  
|**ObjectID**|**int**|Назначенный системой идентификатор объекта, на который была запрошена блокировка, если он доступен и применим.|22|Да|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26||  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, который инициировал сеанс. Например, при подключении к SQL Server с помощью имени Имя_входа1 и выполнении инструкции под именем Имя_входа2 **SessionLoginName** выводит значение Имя_входа1, а функция **LoginName** — значение Имя_входа2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**TextData**|**ntext**|Текстовое значение, зависящее от класса событий, фиксируемых при трассировке.|1|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
