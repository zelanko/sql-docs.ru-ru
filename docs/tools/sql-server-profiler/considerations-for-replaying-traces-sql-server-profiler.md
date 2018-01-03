---
title: "Вопросы воспроизведения трассировки (приложение SQL Server Profiler) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d325c5cd4988764134e4d76dd728a00981e1bc07
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a>Вопросы воспроизведения трассировки (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] не может воспроизводить следующие виды трассировки:  
  
-   Трассировки, содержащие репликацию транзакций и другие виды деятельности, связанной с журналами транзакций. Эти события пропускаются. Другие типы репликации не затрагивают журнала транзакций, поэтому это к ним не относится.  
  
-   Трассировки, содержащие операции, в которых используются идентификаторы GUID. Эти события пропускаются.  
  
-   Трассировки, содержащие операции в столбцах типов данных **text**, **ntext**и **image** и использующие программу **bcp** , инструкции BULK INSERT, READTEXT, WRITETEXT и UPDATETEXT, а также полнотекстовые операции. Эти события пропускаются.  
  
-   Трассировки, включающие в себя привязку сеансов: системные хранимые процедуры **sp_getbindtoken** и **sp_bindsession** . Эти события пропускаются.  
  
> [!NOTE]  
>  Если не используется предварительно настроенный шаблон воспроизведения (**TSQL_Replay**) и не выполняется сбор всех необходимых данных, приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] не воспроизводит трассировку. Дополнительные сведения см. в разделе [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
 Сведения о разрешениях, необходимых для воспроизведения трассировки, см. в разделе [Permissions Required to Run SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).  
  
## <a name="see-also"></a>См. также:  
 [Программа bcp](../../tools/bcp-utility.md)   
 [Руководство по классам событий SQL Server](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [sp_getbindtoken &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql.md)   
 [sp_bindsession (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-bindsession-transact-sql.md)   
 [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [READTEXT &#40; Transact-SQL &#41;](../../t-sql/queries/readtext-transact-sql.md)   
 [Инструкция WRITETEXT &#40; Transact-SQL &#41;](../../t-sql/queries/writetext-transact-sql.md)   
 [UPDATETEXT &#40; Transact-SQL &#41;](../../t-sql/queries/updatetext-transact-sql.md)  
  
  
