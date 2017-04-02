---
title: "Класс событий OLEDB Provider Information | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OLEDB Provider Information, класс событий"
ms.assetid: a0316c4e-4b8c-4754-8a35-222f3c0907d1
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# Класс событий OLEDB Provider Information
  Класс событий **OLEDB Provider Information** имеет место при выполнении распределенного запроса и собирает сведения, относящиеся к соединению поставщика.  
  
 Этот класс событий содержит все свойства, получаемые от удаленного поставщика с использованием различных наборов свойств, включая:  
  
-   DBPROPSET_DATASOURCEINFO  
  
-   SQLPROPSET_OPTHINTS  
  
-   DBPROPSET_SQLSERVERDATASOURCEINFO (только [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])  
  
-   DBPROPSET_SQLSERVERDBINIT (только [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])  
  
-   DBPROPSET_ROWSET  
  
-   IDBInfo interface  
  
 Эти свойства, вместе с доступными метаданными, используются оптимизатором запросов для выбора оптимального плана выполнения запроса. Эти сведения полезны для отслеживания выполнения и анализа вызовов и событий OLE DB при трассировках, выполняемых профилировщиком распределенных запросов.  
  
## Столбцы данных класса событий OLEDB Provider Information  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**ClientProcessID**|**int**|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или *database* по умолчанию, если для данного экземпляра инструкция USE не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**DatabaseName**|**nvarchar**|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|**EventClass**|**int**|Тип события = 194.|27|Нет|  
|**EventSequence**|**int**|Последовательность данного события в запросе.|51|Нет|  
|**GroupID**|**int**|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
|**HostName**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**LinkedServerName**|**nvarchar**|Имя связанного сервера.|45|Да|  
|**LoginName**|**nvarchar**|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], либо учетные данные входа Windows в формате домен\имя_пользователя).|11|Да|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога **sys.server_principals**. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя Windows.|6|Да|  
|**ProviderName**|**nvarchar**|Имя поставщика OLE DB.|46|Да|  
|**RequestID**|**int**|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени Имя_входа1 и при выполнении инструкции под именем Имя_входа2 **SessionLoginName** содержит значение «Имя_входа1», а **LoginName** содержит значение «Имя_входа2». В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
|**TextData**|**ntext**|Текстовое значение, зависящее от класса событий, фиксируемых при трассировке.|1|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
  
## См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Объекты OLE-автоматизации в Transact-SQL](../../relational-databases/stored-procedures/ole-automation-objects-in-transact-sql.md)  
  
  