---
title: Вопросы воспроизведения трассировки (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a485167af34cabca8d616c758e6415117d900f1d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125714"
---
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a>Вопросы воспроизведения трассировки (приложение SQL Server Profiler)
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] не может воспроизводить следующие виды трассировки.  
  
-   Трассировки, содержащие репликацию транзакций и другие виды деятельности, связанной с журналами транзакций. Эти события пропускаются. Другие типы репликации не затрагивают журнала транзакций, поэтому это к ним не относится.  
  
-   Трассировки, содержащие операции, в которых используются идентификаторы GUID. Эти события пропускаются.  
  
-   Трассировки, содержащие операции в столбцах типов данных **text**, **ntext**и **image** и использующие программу **bcp** , инструкции BULK INSERT, READTEXT, WRITETEXT и UPDATETEXT, а также полнотекстовые операции. Эти события пропускаются.  
  
-   Трассировки, включающие в себя привязку сеансов: системные хранимые процедуры **sp_getbindtoken** и **sp_bindsession** . Эти события пропускаются.  
  
> [!NOTE]  
>  Если не используется предварительно настроенный шаблон воспроизведения (**TSQL_Replay**) и не выполняется сбор всех необходимых данных, приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] не воспроизводит трассировку. Дополнительные сведения см. в разделе [Replay Requirements](replay-requirements.md).  
  
 Сведения о разрешениях, необходимых для воспроизведения трассировки, см. в разделе [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).  
  
## <a name="see-also"></a>См. также  
 [bcp Utility](../bcp-utility.md)   
 [Справочник по классам событий SQL Server](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [sp_getbindtoken (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql)   
 [sp_bindsession (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [READTEXT (Transact-SQL)](/sql/t-sql/queries/readtext-transact-sql)   
 [WRITETEXT (Transact-SQL)](/sql/t-sql/queries/writetext-transact-sql)   
 [UPDATETEXT (Transact-SQL)](/sql/t-sql/queries/updatetext-transact-sql)  
  
  
