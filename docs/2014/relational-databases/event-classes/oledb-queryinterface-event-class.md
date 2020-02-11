---
title: Класс событий OLEDB QueryInterface | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- OLEDB QueryInterface event class
ms.assetid: f54c9ef9-3add-497c-a09b-42c4ce3c623d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b420e0b4b9c9531209f3d3227f534116e26dd206
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63032430"
---
# <a name="oledb-queryinterface-event-class"></a>OLEDB QueryInterface, класс событий
  Класс событий **OLEDB QueryInterface** возникает, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вызывает функцию **QueryInterface** OLE DB при обращении к распределенным запросам и удаленным хранимым процедурам. Этот класс событий включается в трассировку, выполняющую наблюдение за проблемами, связанными с выполнением распределенных запросов и удаленных хранимых процедур.  
  
 Когда класс событий **OLEDB QueryInterface** включен в трассировку, значительно возрастает нагрузка на систему. Если такие события происходят часто, трассировка может заметно снизить производительность. Чтобы минимизировать привносимые издержки, используйте этот класс событий только в трассировках, наблюдающих за определенными проблемами в течение непродолжительного периода времени.  
  
## <a name="oledb-queryinterface-event-class-data-columns"></a>Столбцы данных класса событий OLEDB QueryInterface  
  
|Имя столбца данных|Тип данных|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|ClientProcessID|`int`|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|DatabaseID|`int`|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]Отображает имя базы данных, если столбец данных **ServerName** фиксируется при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|имя_базы_данных|`nvarchar`|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|Duration|`bigint`|Продолжительность выполнения события «OLE DB QueryInterface».|13|нет|  
|EndTime|`datetime`|Время окончания события.|15|Да|  
|Ошибка|`int`|Номер ошибки для данного события. Часто это номер ошибки, который хранится в представлении каталога **sys.messages** .|31|Да|  
|EventClass|`int`|Тип события = 120.|27|нет|  
|EventSequence|`int`|Порядковый номер класса событий OLE DB в пакете.|51|нет|  
|EventSubClass|`int`|0 = начало<br /><br /> 1 = завершение|21|нет|  
|GroupID|`int`|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
|HostName|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|IsSystem|`int`|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|LinkedServerName|`nvarchar`|Имя связанного сервера.|45|Да|  
|LoginName|`nvarchar`|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|LoginSid|`image`|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога sys.server_principals. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|MethodName|`nvarchar`|Имя вызывающего метода.|47|нет|  
|NTDomainName|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|NTUserName|`nvarchar`|Имя пользователя Windows.|6|Да|  
|ProviderName|`nvarchar`|Имя поставщика OLE DB.|46|Да|  
|RequestID|`int`|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|SessionLoginName|`nvarchar`|Имя входа пользователя, создавшего этот сеанс. Например, если подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Имя_входа1 и выполнить инструкцию как пользователь с именем Имя_входа2, в столбце `SessionLoginName` выводится значение Имя_входа1, а в столбце `LoginName` — значение Имя_входа2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|SPID|`int`|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|StartTime|`datetime`|Время начала события, если оно известно.|14|Да|  
|TextData|`nvarchar`|Параметры, которые отправляются и принимаются в вызове OLE DB.|1|нет|  
|TransactionID|`bigint`|Назначенный системой идентификатор транзакции.|4|Да|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Объекты OLE-автоматизации в Transact-SQL](../stored-procedures/ole-automation-objects-in-transact-sql.md)  
  
  
