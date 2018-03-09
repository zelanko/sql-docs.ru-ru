---
title: "Класс событий Lock:Escalation | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: event-classes
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Escalation event class
- lock escalation [SQL Server], event class
ms.assetid: d253b44c-7600-4afa-a3a7-03cc937c6a4b
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 90a86e21ca421d50bc94035fb57505630738fbb0
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="lockescalation-event-class"></a>Класс событий Lock:Escalation
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Класс событий **Lock:Escalation** возникает при укрупнении уровня блокировки, например при преобразовании блокировки строки в блокировку объекта. Класс событий Escalation имеет идентификатор события 60.  
  
## <a name="lockescalation-event-class-data-columns"></a>Столбцы данных класса событий Lock:Escalation  
  
|Имя столбца данных|Тип данных|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**ClientProcessID**|**int**|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, в которой запрашивается блокировка. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**DatabaseName**|**nvarchar**|Имя базы данных, где произошло укрупнение уровня блокировки.|35|Да|  
|**EventClass**|**int**|Тип события = 60.|27|нет|  
|**EventSubClass**|**int**|Причина укрупнения блокировки:<br /><br /> **0 — LOCK_THRESHOLD** показывает, что инструкция превысила порог блокировки;<br /><br /> **1 — MEMORY_THRESHOLD** показывает, что инструкция превысила пороговое значение памяти.|21|Да|  
|**EventSequence**|**int**|Последовательность данного события в запросе.|51|нет|  
|**GroupID**|**int**|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
|**HostName**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IntegerData**|**int**|Число блокировок HoBT. Число блокировок для HoBT в момент укрупнения блокировки.|25|Да|  
|**IntegerData2**|**int**|Число укрупненных блокировок. Общее число преобразованных блокировок. Эти структуры блокировок освобождаются, поскольку они уже охватываются укрупненной блокировкой.|55|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**LineNumber**|**int**|Номер строки инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] .|5|Да|  
|**LoginName**|**nvarchar**|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога **sys.server_principals** . Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**Режим**|**int**|Режим блокировки после укрупнения:<br /><br /> 0=NULL — совместим с любыми другими режимами блокировки (LCK_M_NL)<br /><br /> 1 = блокировка стабильности схемы (LCK_M_SCH_S)<br /><br /> 2 = блокировка изменения схемы (LCK_M_SCH_S)<br /><br /> 3 = совмещаемая блокировка (LCK_M_S)<br /><br /> 4 = блокировка обновления (LCK_M_U)<br /><br /> 5 = монопольная блокировка (LCK_M_X)<br /><br /> 6 = коллективная блокировка намерения (LCK_M_IS)<br /><br /> 7 = блокировка намерения обновления (LCK_M_IU)<br /><br /> 8 = монопольная блокировка намерения (LCK_M_IX)<br /><br /> 9 = совмещаемая блокировка с намерением обновления (LCK_M_SIU)<br /><br /> 10 = совмещаемая блокировка с намерением монопольного доступа (LCK_M_SIX)<br /><br /> 11 = блокировка обновления с намерением монопольного доступа (LCK_M_UIX)<br /><br /> 12 = блокировка массового обновления (LCK_M_BU)<br /><br /> 13 = совмещаемая блокировка диапазона ключей — совмещаемая блокировка (LCK_M_RS_S)<br /><br /> 14 = совмещаемая блокировка диапазона ключей — блокировка обновления (LCK_M_RS_U)<br /><br /> 15 = блокировка вставки в диапазон ключей — блокировка NULL (LCK_M_RI_NL)<br /><br /> 16 = блокировка вставки в диапазон ключей — совмещаемая блокировка (LCK_M_RI_S)<br /><br /> 17 = блокировка вставки в диапазон ключей — блокировка обновления (LCK_M_RI_U)<br /><br /> 18 = блокировка вставки в диапазон ключей — монопольная блокировка (LCK_M_RI_X)<br /><br /> 19 = монопольная блокировка диапазона ключей — совмещаемая блокировка (LCK_M_RX_S)<br /><br /> 20 = монопольная блокировка диапазона ключей — блокировка обновления (LCK_M_RX_U)<br /><br /> 21 = монопольная блокировка диапазона ключей — монопольная блокировка (LCK_M_RX_X)|32|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя Windows.|6|Да|  
|**ObjectID**|**int**|Присваиваемый системой идентификатор таблицы, для которой сработало укрупнение блокировки.|22|Да|  
|**ObjectID2**|**bigint**|Идентификатор связанного объекта или сущности. (Идентификатор HoBT, для которого сработало укрупнение блокировки).|56|Да|  
|**Offset**|**int**|Начальное смещение инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] .|61|Да|  
|**OwnerID**|**int**|1 = TRANSACTION<br /><br /> 2 = CURSOR<br /><br /> 3 = SESSION<br /><br /> 4 = SHARED_TRANSACTION_WORKSPACE<br /><br /> 5 = EXCLUSIVE_TRANSACTION_WORKSPACE<br /><br /> 6 = WAITFOR_QUERY|58|Да|  
|**RequestID**|**int**|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|нет|  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2". В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
|**TextData**|**ntext**|Текст инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , которая вызвала укрупнение блокировки.|1|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
|**Тип**|**int**|Гранулярность укрупнения блокировки:<br /><br /> 1 = NULL_RESOURCE<br /><br /> 2 = DATABASE<br /><br /> 3 = FILE<br /><br /> 5 = OBJECT (уровень таблицы)<br /><br /> 6 = PAGE<br /><br /> 7 = KEY<br /><br /> 8 = EXTENT<br /><br /> 9 = RID<br /><br /> 10 = APPLICATION<br /><br /> 11 = METADATA<br /><br /> 12 = HOBT<br /><br /> 13 = ALLOCATION_UNIT|57|Да|  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере используется процедура `sp_trace_create` для создания трассировки, процедура `sp_trace_setevent` для добавления столбцов укрупнения блокировки в трассировку, затем процедура `sp_trace_setstatus` для запуска трассировки. В таких инструкциях, как `EXEC sp_trace_setevent @TraceID, 60, 22, 1`, число `60` показывает класс события укрупнения блокировки, `22` показывает столбец **ObjectID** , а `1` присваивает событию трассировки значение ON.  
  
```  
DECLARE @RC int, @TraceID int;  
EXEC @rc = sp_trace_create @TraceID output, 0, N'C:\TraceResults';  
-- Set the events and data columns you need to capture.  
EXEC sp_trace_setevent @TraceID, 60,  1, 1; --  1 = TextData  
EXEC sp_trace_setevent @TraceID, 60, 12, 1; -- 12 = SPID  
EXEC sp_trace_setevent @TraceID, 60, 21, 1; -- 21 = EventSubClass  
EXEC sp_trace_setevent @TraceID, 60, 22, 1; -- 22 = ObjectID  
EXEC sp_trace_setevent @TraceID, 60, 25, 1; -- 25 = IntegerData  
EXEC sp_trace_setevent @TraceID, 60, 55, 1; -- 25 = IntegerData2  
EXEC sp_trace_setevent @TraceID, 60, 57, 1; -- 57 = Type  
-- Set any filter  byusing sp_trace_setfilter.  
-- Start the trace.  
EXEC sp_trace_setstatus @TraceID, 1;  
GO  
```  
  
 Теперь трассировка работает, можно выполнять необходимые инструкции для трассировки. Когда они завершатся, выполните приведенный ниже код, чтобы остановить и закрыть трассировку. В этом примере значение `fn_trace_getinfo` , используемое в инструкциях `traceid` , получается с помощью функции `sp_trace_setstatus` .  
  
```  
-- After the trace is complete.  
DECLARE @TraceID int;  
-- Find the traceid of the current trace.  
SELECT @TraceID = traceid   
FROM ::fn_trace_getinfo(default)   
WHERE value = N'C:\TraceResults.trc';  
  
-- First stop the trace.   
EXEC sp_trace_setstatus @TraceID, 0;  
  
-- Close and then delete its definition from SQL Server.   
EXEC sp_trace_setstatus @TraceID, 2;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sys.dm_tran_locks (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)  
  
  
