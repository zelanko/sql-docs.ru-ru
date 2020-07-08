---
title: Класс событий Audit Database Object Take Ownership | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Audit Database Object Take Ownership event class
ms.assetid: 26409a60-9616-484b-b608-ca554aef08f6
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7cf4415847421122fd1aa28f4b70c63493924050
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85635631"
---
# <a name="audit-database-object-take-ownership-event-class"></a>Класс событий Audit Database Object Take Ownership
[!INCLUDE [SQL Server - ASDB](../../includes/applies-to-version/sql-asdb.md)]
  Класс событий **Audit Database Object Take Ownership** возникает при смене владельца объектов, расположенных в базе данных.  
  
## <a name="audit-database-object-take-ownership-event-class-data-columns"></a>Столбцы данных класса событий Audit Database Object Take Ownership  
  
|Имя столбца данных|Тип данных|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**DatabaseName**|**nvarchar**|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|**DBUserName**|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|40|Да|  
|**EventSequence**|**int**|Последовательность данного события в запросе.|51|нет|  
|**HostName**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**LoginName**|**nvarchar**|Имя входа пользователя (либо имя входа безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога **sys.server_principals** . Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя Windows.|6|Да|  
|**ObjectName**|**nvarchar**|Имя объекта, на который указывает ссылка.|34|Да|  
|**ObjectType**|**int**|Значение, представляющее тип объекта, связанного с событием. Значение, возвращаемое для этого столбца, представляет собой сочетание соответствующего значения в столбце **type** в представлении каталога **sys.objects** и значений, перечисленных в разделе [Столбец события ObjectType Trace](../../relational-databases/event-classes/objecttype-trace-event-column.md). Например, если возвращается значение 8277-U, тип объекта соответствует пользовательской таблице.|28|Да|  
|**OwnerName**|**nvarchar**|Имя пользователя базы данных, владеющего объектом.|37|Да|  
|**RequestID**|**int**|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|нет|  
|**SessionLoginName**|**Nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2". В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
|**Успешно**|**int**|1 = успешное завершение. 0 = неуспешное завершение. Например, значение 1 означает успешную проверку разрешений, а значение 0 означает, что эта проверка завершена с ошибкой.|23|Да|  
|**TargetUserName**|**nvarchar**|Для действий с пользователем базы данных (например, для предоставления разрешения пользователю) — имя этого пользователя.|39|Да|  
|**TextData**|**ntext**|Текстовое значение, зависящее от класса событий, фиксируемых при трассировке.|1|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
|**XactSequence**|**bigint**|Токен, используемый для описания текущей транзакции.|50|Да|  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
