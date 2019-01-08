---
title: Класс событий OLEDB Call | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- OLEDB Call event class
ms.assetid: e1be1e90-98cc-47a3-addd-59d4aeca6547
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2250847ee35210c63a4ac9ed5e1e41bab33a08ab
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52793296"
---
# <a name="oledb-call-event-class"></a>OLEDB Call, класс событий
  События класса событий **OLEDB Call** происходят, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запрашивает распределенные запросы и удаленные хранимые процедуры у поставщика OLE DB.  
  
 Включайте класс событий **OLEDB Call** для контроля только за теми запросами, которые не посылают запросы и не запрашивают данные, выполненные методом, отличным от **QueryInterface** . При включении в трассировку класса событий **OLEDB Call** количество сигналов зависит от того, насколько часто во время трассировки происходят запросы к базе данных с помощью технологии OLE DB. Если такие вызовы происходят часто, трассировка может заметно снизить производительность.  
  
## <a name="oledb-call-event-class-data-columns"></a>Столбцы данных класса событий OLEDB Call  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|ClientProcessID|`Int`|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|DatabaseID|`Int`|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|DatabaseName|`nvarchar`|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|Duration|`Bigint`|Время, необходимое для выполнения события «Вызов OLE DB».|13|Нет|  
|EndTime|`Datetime`|Время окончания события.|15|Да|  
|Ошибка|`int`|Номер ошибки для данного события. Часто это номер ошибки, который хранится в представлении каталога sys.messages.|31|Да|  
|EventClass|`Int`|Тип события = 119.|27|Нет|  
|EventSequence|`Int`|Порядковый номер класса событий OLE DB в пакете.|51|Нет|  
|EventSubClass|`Int`|0 = начало<br /><br /> 1 = завершение|21|Нет|  
|GroupID|`int`|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
|HostName|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|IsSystem|`int`|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|LinkedServerName|`nvarchar`|Имя связанного сервера.|45|Да|  
|LoginName|`nvarchar`|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате домен\имя_пользователя).|11|Да|  
|LoginSid|`Image`|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога sys.server_principals. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|MethodName|`nvarchar`|Имя метода OLE DB.|47|Да|  
|NTDomainName|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|NTUserName|`nvarchar`|Имя пользователя Windows.|6|Да|  
|ProviderName|`nvarchar`|Имя поставщика OLE DB.|46|Да|  
|RequestID|`Int`|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|SessionLoginName|`nvarchar`|Имя входа пользователя, создавшего этот сеанс. Например, если подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Имя_входа1 и выполнить инструкцию как пользователь с именем Имя_входа2, в столбце `SessionLoginName` выводится значение Имя_входа1, а в столбце `LoginName` — значение Имя_входа2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|SPID|`Int`|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|StartTime|`datetime`|Время начала события, если оно известно.|14|Да|  
|TextData|`nvarchar`|Параметры, которые отправляются и принимаются в вызове OLE DB.|1|Нет|  
|TransactionID|`bigint`|Назначенный системой идентификатор транзакции.|4|Да|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Объекты OLE-автоматизации в Transact-SQL](../stored-procedures/ole-automation-objects-in-transact-sql.md)  
  
  
