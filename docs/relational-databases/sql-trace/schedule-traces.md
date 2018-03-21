---
title: "Планирование трассировок | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-trace
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1d2644b34916c0263b9ae45251050da2331f7f60
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="schedule-traces"></a>Планирование трассировок
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
  
