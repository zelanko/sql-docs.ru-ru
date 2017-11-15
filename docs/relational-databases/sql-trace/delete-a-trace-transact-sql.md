---
title: "Удаление трассировки (Transact-SQL) | Документация Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 452a97ef67be15e2551ce238a3ea37c08998798e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="delete-a-trace-transact-sql"></a>удалить трассировку (Transact-SQL)
  В этом подразделе описано использование хранимых процедур для удаления трассировок.  
  
 Пример использования хранимых процедур трассировки см. в разделе [Создание трассировки (Transact-SQL)](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
### <a name="to-delete-a-trace"></a>Удаление трассировки  
  
1.  Чтобы остановить трассировку, выполните процедуру **sp_trace_setstatus** , указав параметр **@status =0**.  
  
2.  Чтобы закрыть трассировку и удалить сведения о ней с сервера, выполните процедуру **sp_trace_setstatus** , указав параметр **@status =2**.  
  
> [!NOTE]  
>  Перед закрытием трассировка должна быть остановлена.  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры приложения SQL Server Profiler (Transact-SQL)](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  
