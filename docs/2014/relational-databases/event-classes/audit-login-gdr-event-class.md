---
title: Класс событий Audit Login GDR | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Login GDR event class
ms.assetid: cc0560d9-bbb9-4263-a1f3-827c80167f8c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ac1c10bcd56489f9d98415560179b7cf84db0e10
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217564"
---
# <a name="audit-login-gdr-event-class"></a>Audit Login GDR, класс событий
  Класс событий **Audit Login GDR** срабатывает при каждом добавлении или удалении права учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Этот класс событий относится к хранимым процедурам **sp_grantlogin**, **sp_revokelogin**и **sp_denylogin** .  
  
 В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]этот класс событий может быть удален. Вместо этого рекомендуется использовать класс событий **Audit Server Principal Management** .  
  
## <a name="audit-login-gdr-event-class-data-columns"></a>Столбцы данных класса событий Audit Login GDR  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**ClientProcessID**|**int**|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**DatabaseName**|**nvarchar**|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|**EventClass**|**int**|Тип события = 105.|27|Нет|  
|**EventSequence**|**int**|Последовательность данного события в запросе.|51|Нет|  
|**EventSubClass**|**int**|Тип подкласса события.<br /><br /> 1=Разрешить<br /><br /> 2=Отозвать разрешение<br /><br /> 3=Запретить|21|Да|  
|**HostName**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**LoginName**|**nvarchar**|Имя входа пользователя (либо имя входа безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога **sys.server_principals** . Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя Windows.|6|Да|  
|**RequestID**|**int**|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|Нет|  
|**SessionLoginName**|**Nvarchar**|Имя входа пользователя, который инициировал сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2". В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
|**Успешно**|**int**|1 = успешное завершение. 0 = неуспешное завершение. Например, значение 1 означает успешную проверку разрешений, а значение 0 означает, что эта проверка не пройдена.|23|Да|  
|**TargetLoginName**|**nvarchar**|Для действий с именем входа (таких как добавление нового имени входа) — имя входа, с которым совершается действие.|42|Да|  
|**TargetLoginSid**|**image**|SID целевого имени входа.|43|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
|**XactSequence**|**bigint**|Токен, используемый для описания текущей транзакции.|50|Да|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Хранимая процедура sp_grantlogin (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql)   
 [Хранимая процедура sp_revokelogin (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-revokelogin-transact-sql)   
 [Хранимая процедура sp_denylogin (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-denylogin-transact-sql)   
 [Класс событий Audit Server Principal Management](audit-server-principal-management-event-class.md)  
  
  
