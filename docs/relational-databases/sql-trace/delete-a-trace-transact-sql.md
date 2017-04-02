---
title: "удалить трассировку (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "трассировки [SQL Server], удаление"
  - "исключение трассировок"
  - "удаление трассировок"
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# удалить трассировку (Transact-SQL)
  В этом подразделе описано использование хранимых процедур для удаления трассировок.  
  
 Пример использования хранимых процедур трассировки см. в разделе [Создание трассировки (Transact-SQL)](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
### Удаление трассировки  
  
1.  Чтобы остановить трассировку, выполните процедуру **sp_trace_setstatus**, указав **@status = 0**.  
  
2.  Чтобы закрыть трассировку и удалить сведения о ней с сервера, выполните процедуру **sp_trace_setstatus**, указав **@status = 2**.  
  
> [!NOTE]  
>  Перед закрытием трассировка должна быть остановлена.  
  
## См. также:  
 [Хранимая процедура sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры приложения SQL Server Profiler (Transact-SQL)](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  