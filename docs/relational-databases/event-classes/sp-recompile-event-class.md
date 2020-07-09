---
title: Класс событий SP:Recompile | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SP:Recompile event class
ms.assetid: 526c8eae-a07b-4d0e-b91e-8e537835d77d
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7d25f529ddc0bb4e7bc3add5189a5ee9aadccad2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749565"
---
# <a name="sprecompile-event-class"></a>SP:Recompile, класс событий
[!INCLUDE [SQL Server - ASDB](../../includes/applies-to-version/sql-asdb.md)]
  События класса SP:Recompile указывают на то, что хранимая процедура, триггер или пользовательская функция были перекомпилированы. Перекомпиляции, о которых сообщают события этого класса, производятся на уровне инструкций.  
  
 Трассировать повторные компиляции на уровне инструкций предпочтительнее с помощью класса событий SQL:StmtRecompile. Класс событий SP:Recompile использовать не рекомендуется. Дополнительные сведения см. в статье [SQL:StmtRecompile Event Class](../../relational-databases/event-classes/sql-stmtrecompile-event-class.md).  
  
## <a name="sprecompile-event-class-data-columns"></a>Столбцы данных класса событий SP:Recompile  
  
|Имя столбца данных|**Data type**|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|-------------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|ClientProcessID|**int**|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Заполнение этого столбца данных производится в том случае, если клиент предоставляет идентификатор процесса.|9|Да|  
|DatabaseID|**int**|Идентификатор базы данных, в которой выполняется хранимая процедура. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|имя_базы_данных|**nvarchar**|Имя базы данных, в которой выполняется хранимая процедура.|35|Да|  
|EventClass|**int**|Тип события = 37.|27|нет|  
|EventSequence|**int**|Порядковый номер данного события в запросе.|51|нет|  
|EventSubClass|**int**|Тип подкласса события. Указывает причину перекомпиляции.<br /><br /> 1 = изменение схемы<br /><br /> 2 = изменение статистики<br /><br /> 3 = перекомпиляция с разрешением имен<br /><br /> 4 = изменение установленного параметра<br /><br /> 5 = изменение временной таблицы<br /><br /> 6 = изменение удаленного набора строк<br /><br /> 7 = изменение разрешений на обзор<br /><br /> 8 = изменение среды уведомлений о запросах<br /><br /> 9 = изменение представления MPI<br /><br /> 10 = изменение параметров курсора<br /><br /> 11 = по значению параметра перекомпиляции|21|Да|  
|GroupID|**int**|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
|HostName|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|IntegerData2|**int**|Конечное смещение инструкции внутри хранимой процедуры или пакета, вызвавшего повторную компиляцию. Конечное смещение равно -1 в том случае, если инструкция является последней инструкцией в пакете.|55|Да|  
|IsSystem|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|LoginName|**nvarchar**|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|LoginSid|**image**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога sys.server_principals. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|NestLevel|**int**|Уровень вложенности хранимой процедуры.|29|Да|  
|NTDomainName|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|NTUserName|**nvarchar**|Имя пользователя Windows.|6|Да|  
|ObjectID|**int**|Назначенный системой идентификатор хранимой процедуры.|22|Да|  
|ObjectName|**nvarchar**|Имя объекта, запустившего повторную компиляцию.|34|Да|  
|ObjectType|**int**|Значение, представляющее тип объекта, связанного с событием. Дополнительные сведения см. в статье [ObjectType Trace Event Column](../../relational-databases/event-classes/objecttype-trace-event-column.md).|28|Да|  
|Offset|**int**|Начальное смещение инструкции внутри хранимой процедуры или пакета, вызвавшего повторную компиляцию.|61|Да|  
|RequestID|**int**|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|ServerName|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|нет|  
|SessionLoginName|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Login1 и при выполнении инструкции под именем Login2 SessionLoginName будет содержать значение Login1, а LoginName — значение Login2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|SPID|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|SqlHandle|**varbinary**|64-разрядная версия хэша, основанная на тексте нерегламентированного запроса или базы данных и на идентификаторе объекта SQL. Это значение может быть передано в функцию sys.dm_exec_sql_text, чтобы получить связанный SQL-текст.|63|Да|  
|StartTime|**datetime**|Время начала события, если оно известно.|14|Да|  
|TextData|**ntext**|Текст инструкции Transact-SQL, вызвавший перекомпиляцию на уровне инструкции.|1|Да|  
|TransactionID|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
|XactSequence|**bigint**|Токен, используемый для описания текущей транзакции.|50|Да|  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Класс событий SQL:StmtRecompile](../../relational-databases/event-classes/sql-stmtrecompile-event-class.md)  
  
  
