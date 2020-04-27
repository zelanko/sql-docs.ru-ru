---
title: Класс событий SP:StmtStarting | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SP:StmtStarting event class
ms.assetid: 73550597-a3f3-4454-8678-0bf39db80a7f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7acd72b5386eed5e78ddcd2fe1cd0344905fa833
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63050980"
---
# <a name="spstmtstarting-event-class"></a>SP:StmtStarting, класс событий
  Класс событий SP:StmtStarting указывает на то, что в хранимой процедуре запущена инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
## <a name="spstmtstarting-event-class-data-columns"></a>Столбцы данных класса событий SP:StmtStarting  
  
|Имя столбца данных|Тип данных|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|ClientProcessID|`int`|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|DatabaseID|`int`|Идентификатор базы данных, в которой выполняется хранимая процедура. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|имя_базы_данных|`nvarchar`|Имя базы данных, в которой выполняется хранимая процедура.|35|Да|  
|EventClass|`int`|Тип события = 44.|27|Нет|  
|EventSequence|`int`|Последовательность данного события в запросе.|51|Нет|  
|GroupID|`int`|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
|HostName|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|IntegerData2|`int`|Смещение конца выполняемой инструкции (в байтах).|55|Да|  
|IsSystem|`int`|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|LineNumber|`int`|Номер строки выполняемой инструкции.|5|Да|  
|LoginName|`nvarchar`|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|LoginSid|`image`|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога sys.server_principals. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|NestLevel|`int`|Целочисленное значение, представляющее данные, возвращаемые функцией @@NESTLEVEL.|29|Да|  
|NTDomainName|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|NTUserName|`nvarchar`|Имя пользователя Windows.|6|Да|  
|ObjectID|`int`|Идентификатор объекта, назначенный системой.|22|Да|  
|ObjectName|`nvarchar`|Имя объекта, на который указывает ссылка.|34|Да|  
|ObjectType|`int`|Значение, представляющее тип объекта, связанного с событием. Это значение соответствует столбцу типа в представлении каталога sys.objects. Значения см. в разделе [Столбец события ObjectType Trace](objecttype-trace-event-column.md).|28|Да|  
|Offset|`int`|Начальное смещение инструкции в пределах хранимой процедуры или пакета.|61|Да|  
|RequestID|`int`|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|ServerName|`nvarchar`|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|нет|  
|SessionLoginName|`nvarchar`|Имя входа пользователя, создавшего этот сеанс. Например, при соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Login1 и при выполнении инструкции под именем Login2 SessionLoginName будет содержать значение Login1, а LoginName — значение Login2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|SourceDatabaseID|`int`|Идентификатор базы данных, в которой находится объект.|62|Да|  
|SPID|`int`|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|StartTime|`datetime`|Время начала события, если оно известно.|14|Да|  
|Состояние|`int`|Указывает, выполняется ли инструкция после перекомпиляции.<br /><br /> 1 = перекомпиляция выполнена.|30|Да|  
|TextData|`ntext`|Текстовое значение, зависящее от класса событий, фиксируемых при трассировке.|1|Да|  
|TransactionID|`bigint`|Назначенный системой идентификатор транзакции.|4|Да|  
|XactSequence|`bigint`|Токен, используемый для описания текущей транзакции.|50|Да|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
