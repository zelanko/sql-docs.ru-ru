---
title: "Класс событий Audit Schema Object GDR | Документация Майкрософт"
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
- Audit Schema Object GDR event class
ms.assetid: a0187811-dc71-4792-a282-3bfe1ca90c21
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c6162f3dfb48d010c08f5ffa6924ed66c2bff965
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="audit-schema-object-gdr-event-class"></a>Audit Schema Object GDR, класс событий
  События класса **Audit Schema Object GDR** возникают всякий раз, когда выполняются инструкции GRANT, REVOKE или DENY по поводу разрешения для объекта схемы любым пользователем в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="audit-schema-object-gdr-event-class-data-columns"></a>Столбцы данных класса событий Audit Schema Object GDR  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**ClientProcessID**|**int**|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|**ColumnPermissions**|**int**|Указывает, было ли установлено разрешение на доступ к столбцу. Выполните синтаксический анализ текста инструкции, чтобы определить, какие именно разрешения были применены к тем или иным столбцам. 1 = да, 0 = нет.|44|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**DatabaseName**|**nvarchar**|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|**DBUserName**|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|40|Да|  
|**EventClass**|**int**|Тип события = 103.|27|Нет|  
|**EventSequence**|**int**|Последовательность данного события в запросе.|51|Нет|  
|**EventSubClass**|**int**|Тип подкласса события.<br /><br /> 1=Разрешить<br /><br /> 2=Отозвать разрешение<br /><br /> 3=Запретить|21|Да|  
|**HostName**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**LoginName**|**nvarchar**|Имя входа пользователя (либо имя входа безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога **sys.server_principals** . Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя Windows.|6|Да|  
|**ObjectName**|**nvarchar**|Имя объекта, являющегося предметом разрешения, отмены разрешения или запрета разрешения.|34|Да|  
|**ObjectType**|**int**|Значение, представляющее тип объекта, связанного с событием. Это значение соответствует столбцу типа в представлении каталога **sys.objects** . Значения см. в разделе [Столбец события ObjectType Trace](../../relational-databases/event-classes/objecttype-trace-event-column.md).|28|Да|  
|**OwnerName**|**nvarchar**|Имя пользователя базы данных, присвоенное владельцу объекта, являющегося предметом разрешения, отмены разрешения или запрета разрешения.|37|Да|  
|**ParentName**|**nvarchar**|Имя схемы, в которой находится объект.|59|Да|  
|**Разрешения**|**bigint**|Целочисленное значение, отражающее тип проверяемых разрешений.<br /><br /> 1 = SELECT ALL<br /><br /> 2 = UPDATE ALL<br /><br /> 4 = REFERENCES ALL<br /><br /> 8 = INSERT<br /><br /> 16 = DELETE<br /><br /> 32 = EXECUTE (только для процедур)<br /><br /> 4096 = SELECT ANY (минимум один столбец)<br /><br /> 8192 = UPDATE ANY<br /><br /> 16384 = REFERENCES ANY|19|Да|  
|**RequestID**|**int**|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|Нет|  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени Имя_входа1 и при выполнении инструкции под именем Имя_входа2 **SessionLoginName** содержит значение «Имя_входа1», а **LoginName** содержит значение «Имя_входа2». В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
|**Успешно**|**int**|1 = успешное завершение. 0 = неуспешное завершение. Например, значение 1 означает успешную проверку разрешений, а значение 0 означает, что эта проверка не пройдена.|23|Да|  
|**TargetLoginName**|**nvarchar**|Для действий с именем входа (таких как добавление нового имени входа) — имя входа, с которым совершается действие.|42|Да|  
|**TargetLoginSid**|**image**|Для действий с именем входа (таких как добавление нового имени входа) — идентификатор безопасности имени входа, с которым совершается действие.|43|Да|  
|**TargetUserName**|**nvarchar**|Для действий с пользователем базы данных (например, для предоставления разрешения пользователю) — имя этого пользователя.|39|Да|  
|**TextData**|**ntext**|Текстовое значение, зависящее от класса событий, фиксируемых при трассировке.|1|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
|**XactSequence**|**bigint**|Токен, используемый для описания текущей транзакции.|50|Да|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)   
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)  
  
  
