---
title: Использование сеанса system_health | Документация Майкрософт
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: tutorial
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 262860781ba99abf8c4f6de783cd477db0e15d81
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68009348"
---
# <a name="use-the-systemhealth-session"></a>Использование сеанса system_health

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Сеанс system_health является сеансом расширенных событий, который по умолчанию включен в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот сеанс запускается автоматически при запуске [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и выполняется без заметного воздействия на производительность. В этом сеансе собираются системные данные, которые можно использовать для устранения неполадок, связанных с производительностью компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. 

> [!IMPORTANT]
> Поэтому этот сеанс не рекомендуется останавливать или удалять.  
  
Сеанс собирает следующие данные.  
  
-   *sql_text* и *session_id* для всех сеансов, в которых возникает ошибка с уровнем серьезности >= 20.  
  
-   *sql_text* и *session_id* для всех сеансов, в которых возникает ошибка, связанная с памятью. К этим ошибкам относятся 17803, 701, 802, 8645, 8651, 8657 и 8902.  
  
-   Запись всех нерешенных проблем планировщика. Они записываются в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виде ошибки 17883.  
  
-   Все обнаруженные взаимоблокировки, включая граф взаимоблокировок.  
  
-   *callstack*, *sql_text* и *session_id* для всех сеансов, которые ожидали снятия кратковременной блокировки (или других необходимых ресурсов) более 15 секунд.  
  
-   *callstack*, *sql_text* и *session_id* для всех сеансов, которые ожидали снятия блокировки более 30 секунд.  
  
-   *callstack*, *sql_text* и *session_id* для всех сеансов, которые долгое время находились в режиме ожидания с вытеснением. Длительность зависит от типа ожидания. Ожидание с вытеснением возникает в том случае, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ожидает внешних вызовов API.  
  
-   Значения *callstack* и *session_id* для ошибок размещения CLR и виртуального выделения.  
  
-   События ring_buffer для брокера памяти, монитора планировщиков, OOM узла памяти, безопасности и возможности подключения.  
  
-   Компонент системы результирует из `sp_server_diagnostics`.  
  
-   Данные об исправности экземпляра, собираемые *scheduler_monitor_system_health_ring_buffer_recorded*.  
  
-   Сбои размещения CLR.  
  
-   Ошибки возможности подключения при использовании *connectivity_ring_buffer_recorded*.  
  
-   Ошибки безопасности при использовании *security_error_ring_buffer_recorded*.  

> [!NOTE]
> Дополнительные сведения о взаимоблокировках см. в [разделе о взаимоблокировке в руководстве по блокировке и управлению версиями строк транзакций](../../relational-databases/sql-server-transaction-locking-and-row-versioning-guide.md#deadlocks).   
> Дополнительные сведения о сообщениях об ошибках SQL см. в разделе [Ошибки ядра СУБД](../../relational-databases/errors-events/database-engine-events-and-errors.md).

## <a name="viewing-the-session-data"></a>Просмотр данных сеанса  
В сеансе для хранения данных используется целевой кольцевой буфер и целевой файл событий. Целевой файл событий имеет максимальный размер 5 МБ и политику хранения файлов — 4 файла. 

Для просмотра данных сеанса из целевого кольцевого буфера с пользовательским интерфейсом расширенных событий, доступным в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], см. раздел [Расширенный просмотр целевых данных из расширенных событий в SQL Server – просмотр динамических данных](../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md#b3-watch-live-data).

Для просмотра данных сеанса из кольцевого буфера с [!INCLUDE[tsql](../../includes/tsql-md.md)] используйте следующий запрос:  
  
```sql  
SELECT CAST(xet.target_data as xml) 
FROM sys.dm_xe_session_targets xet  
JOIN sys.dm_xe_sessions xe ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'system_health'  
```  
  
Для просмотра данных сеанса из файла событий пользуйтесь доступным пользовательским интерфейсом расширенных событий в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Advanced Viewing of Target Data from Extended Events in SQL Server](../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md)(Расширенный просмотр целевых данных из расширенных событий в SQL Server).
  
## <a name="restoring-the-systemhealth-session"></a>Восстановление сеанса system_health  
Если сеанс system_healt был удален, то вы можете его восстановить, выполнив файл **u_tables.sql** в редакторе запросов. Этот файл находится в следующей папке, где **C:** означает диск, на котором установлены программные файлы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а **MSSQL1x** — основной номер версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
 `C:\Program Files\Microsoft SQL Server\MSSQL1x.\<*instanceid*>\MSSQL\Install`  
  
Имейте в виду, что после восстановления сеанса необходимо его запустить с помощью инструкции `ALTER EVENT SESSION` или через узел **Расширенные события** в обозревателе объектов. Если этого не сделать, сеанс запустится автоматически при следующем перезапуске службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)    
 [Средства расширенных событий](../../relational-databases/extended-events/extended-events-tools.md)    
 [Ошибки ядра СУБД](../../relational-databases/errors-events/database-engine-events-and-errors.md)    
 [Представления каталога сообщений (для ошибок) — sys.messages](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md) 
