---
title: "Планирование трассировок | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], events
- traces [SQL Server]
- traces [SQL Server], stopping
- events [SQL Server], filters
- scheduling traces [SQL Server]
- traces [SQL Server], scheduling
- stopping traces
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8bbb42de736fd7c330c87380dc7203198062f3da
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="schedule-traces"></a>Планирование трассировок
  В Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]предусмотрены два способа планирования трассировок. Возможные действия:  
  
-   задать время прекращения трассировки;  
  
-   использовать агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для планирования трассировки.  
  
## <a name="specifying-a-stop-time"></a>Задание времени прекращения  
 Время прекращения трассировки можно указать в том случае, если используются хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] или приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Время прекращения указывается после того, как произведено начальное конфигурирование трассировки.  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a>Планирование трассировки с помощью агента SQL Server  
 Наилучшим способом планирования трассировок является использование агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для запуска трассировки с последующим указанием времени ее прекращения хранимой процедурой [!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_trace_setstatus**или приложением [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 **Установка фильтра времени прекращения трассировки**  
  
 [Фильтровать события по времени окончания (приложение SQL Server Profiler)](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [Хранимая процедура sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Задачи автоматизированного администрирования (агент SQL Server)](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)  
  
  

