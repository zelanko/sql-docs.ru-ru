---
title: Класс событий Audit Login Change Property | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Audit Login Change Property event class
ms.assetid: 47c8f045-37e5-471e-bf01-55d988ed47c1
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0da4693597cdbf46d7754d965ac706a6969c434e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43084614"
---
# <a name="audit-login-change-property-event-class"></a>Audit Login Change Property, класс событий
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Класс событий **Audit Login Change Property** происходит при запуске хранимых процедур **sp_defaultdb** и **sp_defaultlanguage** или инструкции ALTER LOGIN для изменения свойства имени входа.  
  
## <a name="audit-login-change-property-event-class-data-columns"></a>Столбцы класса событий Audit Login Change Property  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**ClientProcessID**|**int**|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**DatabaseName**|**nvarchar**|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|**EventClass**|**int**|Тип события = 106.|27|нет|  
|**EventSequence**|**int**|Последовательность данного события в запросе.|51|нет|  
|**EventSubClass**|**int**|Тип подкласса события.<br /><br /> 1=изменилась база данных по умолчанию<br /><br /> 2=изменился язык по умолчанию<br /><br /> 3=изменилось имя<br /><br /> 4=изменились учетные данные<br /><br /> 5=изменилась политика<br /><br /> 6=изменилось истечение срока действия|21|Да|  
|**HostName**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**LoginName**|**nvarchar**|Имя входа пользователя (либо имя входа безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога **sys.server_principals** . Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя Windows.|6|Да|  
|**ObjectName**|**nvarchar**|Имя объекта, на который указывает ссылка.|34|Да|  
|**ObjectType**|**int**|Значение, представляющее тип объекта, связанного с событием. Это значение соответствует столбцу типа в представлении каталога **sys.objects** . Значения см. в разделе [Столбец события ObjectType Trace](../../relational-databases/event-classes/objecttype-trace-event-column.md).|28|Да|  
|**OwnerName**|**nvarchar**|Имя пользователя базы данных, владеющего объектом.|37|Да|  
|**RequestID**|**int**|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|нет|  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2". В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
|**Успешно**|**int**|1 = успешное завершение. 0 = неуспешное завершение. Например, значение 1 означает успешную проверку разрешений, а значение 0 означает, что эта проверка не пройдена.|23|Да|  
|**TargetLoginName**|**nvarchar**|Для действий с именем входа (таких как добавление нового имени входа) — имя входа, с которым совершается действие.|42|Да|  
|**TargetLoginSid**|**image**|Для действий с именем входа (таких как добавление нового имени входа) — идентификатор безопасности имени входа, с которым совершается действие.|43|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
|**XactSequence**|**bigint**|Токен, используемый для описания текущей транзакции.|50|Да|  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_defaultdb (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md)   
 [sp_defaultlanguage (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-defaultlanguage-transact-sql.md)  
  
  
