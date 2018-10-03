---
title: Класс событий Showplan XML for Query Compile | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Showplan XML For Query Compile event class
ms.assetid: 48919fcb-3a22-43ca-a63c-b210cf2c32d5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 78b7f0027b92671328b835aa7ec2af6695eb3eea
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48081964"
---
# <a name="showplan-xml-for-query-compile-event-class"></a>Showplan XML For Query Compile, класс событий
  Класс событий Showplan XML For Query Compile происходит, когда [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компилирует инструкцию SQL. Включите этот класс событий, чтобы идентифицировать операторы инструкции Showplan в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Класс событий Showplan XML For Query Compile выводит полные данные, относящиеся ко времени компиляции, поэтому трассировки, содержащие этот класс событий, могут повлечь за собой значительные издержки производительности. Чтобы уменьшить этот эффект, используйте данный класс событий только в тех трассировках, которые применяются для наблюдения за конкретными проблемами в течение непродолжительного времени.  
  
 Документы Showplan XML имеют схему, связанную с ними. Эта схема находится на [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkId=41740)или является частью установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="showplan-xml-for-query-compile-event-class-data-columns"></a>Столбцы данных класса событий «XML-код инструкции Showplan компиляции запроса»  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|BinaryData|`image`|Предполагаемая стоимость запроса.|2|Нет|  
|ClientProcessID|`int`|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.|9|Да|  
|DatabaseID|`int`|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database*не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных ServerName захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|DatabaseName|`nvarchar`|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|Класс событий|`int`|Тип события = 168.|27|Нет|  
|EventSequence|`int`|Последовательность данного события в запросе.|51|Нет|  
|HostName|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|IntegerData|`int`|Предполагаемое количество возвращаемых строк.|25|Да|  
|IsSystem|`int`|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|LineNumber|`int`|Отображает номер строки, содержащей ошибку.|5|Да|  
|LoginName|`nvarchar`|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|LoginSID|`image`|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога sys.server_principals. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Нет|  
|NestLevel|`int`|Целочисленное значение, представляющее данные, возвращаемые функцией @@NESTLEVEL.|29|Да|  
|NTDomainName|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|NTUserName|`nvarchar`|Имя пользователя Windows.|6|Да|  
|ObjectID|`int`|Идентификатор объекта, назначенный системой.|22|Да|  
|ObjectName|`nvarchar`|Имя объекта, на который указывает ссылка.|34|Да|  
|ObjectType|`int`|Значение, представляющее тип объекта, связанного с событием. Это значение соответствует столбцу type в таблице sys.objects. Значения см. в статье [Столбец события ObjectType Trace](objecttype-trace-event-column.md).|28|Да|  
|RequestID|`int`|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|ServerName|`nvarchar`|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|Нет|  
|SessionLoginName|`nvarchar`|Имя входа пользователя, создавшего этот сеанс. Например, при соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Login1 и при выполнении инструкции под именем Login2 SessionLoginName будет содержать значение Login1, а LoginName — значение Login2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|SPID|`int`|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|StartTime|`datetime`|Время начала события, если оно известно.|14|Да|  
|TextData|`ntext`|Текстовое значение, зависящее от класса событий, фиксируемых при трассировке.|1|Да|  
|TransactionID|`bigint`|Назначенный системой идентификатор транзакции.|4|Да|  
|XactSequence|`bigint`|Токен, используемый для описания текущей транзакции.|50|Да|  
|GroupID|`int`|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Справочник по логическим и физическим операторам Showplan](../showplan-logical-and-physical-operators-reference.md)  
  
  
