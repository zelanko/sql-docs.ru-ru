---
title: "Класс событий SQL:BatchCompleted | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: event-classes
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQL:BatchCompleted event class
ms.assetid: 1be023e8-7a98-4400-b9e7-b24f6a3fc5ca
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 27d81d35cbf12b5315ad05bca3122285fe4394bd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sqlbatchcompleted-event-class"></a>SQL:BatchCompleted, класс событий
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] Класс событий SQL:BatchCompleted указывает на завершение выполнения пакета языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="sqlbatchcompleted-event-class-data-columns"></a>Столбцы данных класса событий SQL:BatchCompleted  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|ClientProcessID|**int**|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|ЦП|**int**|Количество времени ЦП (в миллисекундах), использованного пакетом.|18|Да|  
|DatabaseID|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных ServerName захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|DatabaseName|**nvarchar**|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|Длительность|**bigint**|Длительность события (в микросекундах).|13|Да|  
|EndTime|**datetime**|Время окончания события. Этот столбец не заполняется для таких классов событий запуска, как SQL:BatchStarting или SP:Starting.|15|Да|  
|Ошибка|**int**|Номер ошибки события.<br /><br /> 0 = ОК<br /><br /> 1 = ошибка<br /><br /> 2 = прервано|31|Да|  
|EventClass|**int**|Тип события = 12.|27|Нет|  
|EventSequence|**int**|Последовательность данного события в запросе.|51|Нет|  
|GroupID|**int**|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
|HostName|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|IsSystem|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|LoginName|**nvarchar**|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|LoginSid|**image**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога sys.server_principals. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|NTDomainName|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|NTUserName|**nvarchar**|Имя пользователя Windows.|6|Да|  
|Reads|**bigint**|Число операций чтения страниц, вызванных пакетом.|16|Да|  
|RequestID|**int**|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|RowCounts|**bigint**|Количество строк, затронутых событием.|48|Да|  
|ServerName|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|Нет|  
|SessionLoginName|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Login1 и при выполнении инструкции под именем Login2 SessionLoginName будет содержать значение Login1, а LoginName — значение Login2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|SPID|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|StartTime|**datetime**|Время начала события, если оно известно.|14|Да|  
|TextData|**ntext**|Текст пакета.|1|Да|  
|TransactionID|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
|Writes|**bigint**|Количество операций записи страниц, вызванных пакетом.|17|Да|  
|XactSequence|**bigint**|Токен, который описывает текущую транзакцию.|50|Да|  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
