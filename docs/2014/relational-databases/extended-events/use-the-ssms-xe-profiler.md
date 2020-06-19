---
title: Использование сеанса system_health | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
author: yualan
ms.author: alayu
ms.openlocfilehash: 5f96be882208a9570c36ef8da63f1efb265f752f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85027258"
---
# <a name="use-the-system_health-session"></a>Использование сеанса system_health
  Сеанс system_health является сеансом расширенных событий, который по умолчанию включен в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот сеанс запускается автоматически при запуске [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и выполняется без заметного воздействия на производительность. В этом сеансе собираются системные данные, которые можно использовать для устранения неполадок, связанных с производительностью компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Поэтому этот сеанс не рекомендуется останавливать или удалять.  
  
 Сеанс собирает следующие данные.  
  
-   sql_text и session_id для всех сеансов, в которых возникает ошибка с уровнем серьезности >=20.  
  
-   sql_text и session_id для всех сеансов, в которых возникает ошибка, связанная с памятью. К этим ошибкам относятся 17803, 701, 802, 8645, 8651, 8657 и 8902.  
  
-   Запись всех нерешенных проблем планировщика. (Они записываются в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виде ошибки 17883.)  
  
-   Все обнаруженные взаимоблокировки.  
  
-   callstack, sql_text и session_id для всех сеансов, которые ожидали снятия кратковременной блокировки (или других необходимых ресурсов) более 15 с.  
  
-   callstack, sql_text и session_id для всех сеансов, которые ожидали снятия блокировки более 30 с.  
  
-   callstack, sql_text и session_id для всех сеансов, которые долгое время находились в режиме ожидания с вытеснением. Длительность зависит от типа ожидания. Ожидание с вытеснением возникает в том случае, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ожидает внешних вызовов API.  
  
-   Значения callstack и session_id для ошибок размещения CLR и виртуального выделения.  
  
-   События ring_buffer для брокера памяти, монитора планировщиков, OOM узла памяти, безопасности и возможности подключения.  
  
-   Результаты из sp_server_diagnostics.  
  
-   Данные об исправности экземпляра, собираемые scheduler_monitor_system_health_ring_buffer_recorded.  
  
-   Сбои размещения CLR.  
  
-   Ошибки возможности подключения при использовании connectivity_ring_buffer_recorded.  
  
-   Ошибки безопасности при использовании security_error_ring_buffer_recorded.  
  
## <a name="viewing-the-session-data"></a>Просмотр данных сеанса  
 В сеансе для хранения данных используется цель «Кольцевой буфер». Для просмотра данных сеанса используйте следующий запрос.  
  
```  
SELECT CAST(xet.target_data as xml) FROM sys.dm_xe_session_targets xet  
JOIN sys.dm_xe_sessions xe  
ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'system_health'  
```  
  
 Для просмотра данных сеанса событий из файла пользуйтесь доступным пользовательским интерфейсом расширенных событий в среде Management Studio. Подробнее см. в разделе [View Event Session Data](../../database-engine/view-event-session-data.md) .  
  
## <a name="restoring-the-system_health-session"></a>Восстановление сеанса system_health  
 Если сеанс system_healt был удален, то вы можете его восстановить, выполнив файл **u_tables.sql** в редакторе запросов. Этот файл находится в следующей папке (где C: означает диск, на котором установлены программные файлы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ):  
  
 C:\Program Files\Microsoft SQL Server\MSSQL12. \<*instanceid*> \мсскл\инсталл  
  
 Имейте в виду, что после восстановления сеанса необходимо его запустить с помощью инструкции ALTER EVENT SESSION или через узел **Расширенные события** в обозревателе объектов. Если этого не сделать, сеанс запустится автоматически при следующем перезапуске службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Средства расширенных событий](extended-events-tools.md)  
  
  
