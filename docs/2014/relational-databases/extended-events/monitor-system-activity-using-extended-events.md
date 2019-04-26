---
title: Мониторинг активности системы с помощью расширенных событий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- xe
- extended events [SQL Server], monitoring system activity
ms.assetid: d83ad88f-818c-49fe-a9a9-299f704fca53
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44bb482d1385ad9b22900bb74015a779ea6750d7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62638736"
---
# <a name="monitor-system-activity-using-extended-events"></a>отслеживать активность системы с помощью расширенных событий
  Эта процедура показывает, как использовать расширенные события совместно со средством отслеживания событий для Windows (ETW) в целях мониторинга активности системы. Процедура показывает также варианты использования инструкций CREATE EVENT SESSION, ALTER EVENT SESSION и DROP EVENT SESSION.  
  
 Решение этих задач предполагает использование редактора запросов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для выполнения следующей процедуры. Процедура требует также использования командной строки для выполнения команд ETW.  
  
### <a name="to-monitor-system-activity-using-extended-events"></a>Мониторинг активности системы с помощью расширенных событий  
  
1.  В редакторе запросов выполните следующие инструкции, чтобы создать сеанс событий и добавить два события. Эти события (checkpoint_begin и checkpoint_end) запускаются в начале и в конце контрольной точки базы данных.  
  
    ```  
    CREATE EVENT SESSION test0  
    ON SERVER  
    ADD EVENT sqlserver.checkpoint_begin,  
    ADD EVENT sqlserver.checkpoint_end  
    WITH (MAX_DISPATCH_LATENCY = 1 SECONDS)  
    go  
    ```  
  
2.  Добавьте цель сегментирования с 32 сегментами для подсчета числа контрольных точек по идентификатору базы данных.  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.histogram  
    (  
          SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id'  
    )  
    go  
    ```  
  
3.  Выполните следующие инструкции, чтобы добавить цель ETW. Это позволит видеть события начала и конца и использовать это для определения продолжительности обработки контрольной точки.  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.etw_classic_sync_target  
    go  
    ```  
  
4.  Введите следующие инструкции, чтобы запустить сеанс и начать сбор событий.  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = start  
    go  
    ```  
  
5.  Введите следующие инструкции для запуска трех событий.  
  
    ```  
    USE tempdb  
          checkpoint  
    go  
    USE master  
          checkpoint  
          checkpoint  
    go  
    ```  
  
6.  Введите следующие инструкции для просмотра счетчиков событий.  
  
    ```  
    SELECT CAST(xest.target_data AS xml) Bucketizer_Target_Data_in_XML  
    FROM sys.dm_xe_session_targets xest  
    JOIN sys.dm_xe_sessions xes ON xes.address = xest.event_session_address  
    JOIN sys.server_event_sessions ses ON xes.name = ses.name  
    WHERE xest.target_name = 'histogram' AND xes.name = 'test0'  
    go  
    ```  
  
7.  В командной строке введите следующие команды для просмотра данных EWT.  
  
    > [!NOTE]  
    >  Чтобы получить справку по команде **tracerpt** , введите в командной строке команду `tracerpt /?`.  
  
    ```  
    logman query -ets --- List the ETW sessions. This is optional.  
    logman update XE_DEFAULT_ETW_SESSION -fd -ets --- Flush the ETW log.  
    tracerpt %temp%\xeetw.etl -o xeetw.txt --- Dump the events so they can be seen.  
    ```  
  
8.  Введите следующие инструкции, чтобы прекратить сеанс и удалить его с сервера.  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = STOP  
    go  
  
    DROP EVENT SESSION test0  
    ON SERVER  
    go  
    ```  
  
## <a name="see-also"></a>См. также  
 [CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [DROP EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/drop-event-session-transact-sql)   
 [Представления каталога расширенных событий (Transact-SQL)](/sql/relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql)  
 [Динамические административные представления расширенных событий](../views/views.md)   
 [Цели расширенных событий SQL Server](../../database-engine/sql-server-extended-events-targets.md)  
  
  
