---
title: "KILL (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/31/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- KILL_TSQL
- KILL
dev_langs: TSQL
helpviewer_keywords:
- WITH STATUSONLY option
- terminating distributed transactions
- distributed transactions [SQL Server], terminating
- in-doubt transactions
- IDs [SQL Server], user processes
- ending distributed transactions [SQL Server]
- stopping distributed transactions
- session IDs [SQL Server]
- system process termination [SQL Server]
- stopping processes
- ending processes [SQL Server]
- UOW [SQL Server]
- orphaned transactions [SQL Server]
- unit of work [SQL Server]
- process termination [SQL Server]
- KILL statement
- terminating process
ms.assetid: 071cf260-c794-4b45-adc0-0e64097938c0
caps.latest.revision: "61"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: c05f03abc5bb03da332ba2ec28294ea7af3f9d1e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="kill-transact-sql"></a>KILL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Прерывает пользовательский процесс, определяемый идентификатором сеанса или единицей работы (UOW). Если указанный сеанса или UOW объем работы для отмены, инструкции KILL может занять некоторое время, особенно если он включает в себя отката длительной транзакции.  
  
 С помощью инструкции KILL можно завершить нормальное соединение, которое внутренне завершит транзакции, связанные с заданным идентификатором сеанса. Инструкция может также использоваться для завершения потерянных и сомнительных распределенных транзакций при [!INCLUDE[msCoName](../../includes/msconame-md.md)] координатора распределенных транзакций (MS DTC) уже используется.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
KILL { session ID | UOW } [ WITH STATUSONLY ]   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
KILL 'session_id'  
[;]   
```  
  
## <a name="arguments"></a>Аргументы  
 *Идентификатор сеанса*  
 Идентификатор сеанса завершаемого процесса. *Идентификатор сеанса* является уникальным целым числом (**int**), назначается каждому соединению пользователя при установке соединения. Значение идентификатора сеанса остается привязанным к соединению в течение всего времени соединения. По окончании соединения данное целое значение освобождается и может быть присвоено другому соединению.  
Следующий запрос может помочь выявить `session_id` , которую требуется удалить:  
 ```sql  
 SELECT conn.session_id, host_name, program_name,
     nt_domain, login_name, connect_time, last_request_end_time 
FROM sys.dm_exec_sessions AS sess
JOIN sys.dm_exec_connections AS conn
    ON sess.session_id = conn.session_id;
```  
  
*UOW*  
**Применяется к**: ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Задает идентификатор единицы работы (UOW) распределенных транзакций. *UOW* представляет собой идентификатор GUID, который может быть получен из столбца request_owner_guid динамического административного представления sys.dm_tran_locks. *UOW* также может быть получен из журнала ошибок или из монитора транзакций MS DTC. Дополнительные сведения о наблюдении за распределенными транзакциями см. в руководстве пользователя MS DTC.  
  
 Используйте инструкцию KILL *UOW* для завершения потерянных распределенных транзакций. Эти транзакции не связаны с идентификаторами реальных сеансов, но искусственно связаны с идентификатором сеанса -2. Этот идентификатор упрощает поиск потерянных транзакций с помощью запроса столбца идентификатора сеанса из динамических административных представлений sys.dm_tran_locks, sys.dm_exec_sessions или sys.dm_exec_requests.  
  
 WITH STATUSONLY  
 Создает отчет о ходе выполнения о указанного *идентификатор сеанса* или *UOW* , производится откат из-за выполненной ранее инструкции KILL. Инструкция KILL WITH STATUSONLY не завершает и откат *идентификатор сеанса* или *UOW*; команда только отображает текущее состояние отката.  
  
## <a name="remarks"></a>Замечания  
 Инструкция KILL обычно используется для прерывания процессов, блокирующих другие важные процессы или выполняющих запросы, занимающие необходимые системные ресурсы. Системные процессы и процессы, выполняющие расширенные хранимые процедуры, не могут быть прерваны.  
  
 Используйте инструкцию KILL осторожно, особенно если запущены критические процессы. Существует опасность прерывания собственного процесса. Не нужно прерывать следующие процессы:  
  
-   AWAITING COMMAND  
-   CHECKPOINT SLEEP  
-   LAZY WRITER  
-   LOCK MONITOR;  
-   SIGNAL HANDLER  
  
Используйте @@SPID для отображения значения идентификатора сеанса для текущего сеанса.  
  
 Чтобы получить отчет о значениях идентификаторов активных сеансов, можно запросить столбец session_id из динамических административных представлений sys.dm_tran_locks, sys.dm_exec_sessions и sys.dm_exec_requests. Также можно посмотреть столбец SPID, возвращаемый системной хранимой процедурой sp_who. Если откат выполняется для конкретного SPID, столбец cmd результирующего sp_who задать для что SPID указывает KILLED/ROLLBACK.  
  
 Если какое-либо соединение имеет блокировку на ресурс базы данных и блокирует обработку остальных соединений, идентификаторы сеансов заблокированных соединений появятся в столбце `blocking_session_id` представления `sys.dm_exec_requests` или в столбце `blk`, возвращенном хранимой процедурой `sp_who`.  
  
 Инструкцию KILL можно применять для решения проблем с сомнительными распределенными транзакциями. Эти транзакции представляют собой неразрешимые распределенные транзакции, возникшие в результате незапланированных повторных стартов сервера баз данных или координатора MS DTC. Дополнительные сведения о проблемных транзакциях см. в подразделе «Двухфазная фиксация» [использование помеченных транзакций для согласованного восстановления связанных баз данных &#40; Модель полного восстановления &#41; ](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
## <a name="using-with-statusonly"></a>Использование предложения WITH STATUSONLY  
 Инструкция KILL WITH STATUSONLY создает отчет только в том случае, если идентификатор сеанса или UOW в данный момент производится откат из-за ранее инструкцией KILL *идентификатор сеанса*|*UOW* инструкции. Отчет о состоянии отображает процесс выполнения отката (в процентах), а также выводит ожидаемое время до окончания операции (в секундах) в следующей форме:  
  
 `Spid|UOW <xxx>: Transaction rollback in progress. Estimated rollback completion: <yy>% Estimated time left: <zz> seconds`  
  
 Если откат сеанса или UOW завершен к моменту выполнения инструкции KILL *идентификатор сеанса*|*UOW* выполняется инструкция WITH STATUSONLY, или если нет идентификатор сеанса или UOW производится откат, KILL *идентификатор сеанса*|*UOW* WITH STATUSONLY возвращает следующую ошибку:  
  
 ```
"Msg 6120, Level 16, State 1, Line 1"  
"Status report cannot be obtained. Rollback operation for Process ID <session ID> is not in progress."
```  
  
 Аналогичный отчет о состоянии может быть получен при повторном выполнении инструкции KILL *идентификатор сеанса*|*UOW* без использования параметра WITH STATUSONLY, однако не рекомендуется делать это. Повторение KILL *идентификатор сеанса* инструкция может вызвать завершение нового процесса, если процесс отката был завершен, и идентификатор сеанса было присвоено новой задачи до запуска новой инструкции KILL. Указание параметра WITH STATUSONLY предотвращает указанные последствия.  
  
## <a name="permissions"></a>Permissions  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:** Необходимо разрешение ALTER ANY CONNECTION. Разрешение ALTER ANY CONNECTION включено с членством в предопределенных ролях сервера sysadmin или processadmin.  
  
 **[!INCLUDE[ssSDS](../../includes/sssds-md.md)]:** Требуется разрешение KILL DATABASE CONNECTION. Имя входа субъекта серверного уровня имеет KILL DATABASE CONNECTION.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-kill-to-terminate-a-session"></a>A. Использование инструкции KILL для завершения сеанса  
 Следующий пример показывает завершение сеанса с идентификатором `53`.  
  
```sql  
KILL 53;  
GO  
```  
  
### <a name="b-using-kill-session-id-with-statusonly-to-obtain-a-progress-report"></a>Б. Использование инструкции KILL SPID WITH STATUSONLY для получения отчета о состоянии  
 В данном примере создается отчет о состоянии процесса отката указанного сеанса.  
  
```sql  
KILL 54;  
KILL 54 WITH STATUSONLY;  
GO  
  
--This is the progress report.  
spid 54: Transaction rollback in progress. Estimated rollback completion: 80% Estimated time left: 10 seconds.  
```  
  
### <a name="c-using-kill-to-terminate-an-orphaned-distributed-transaction"></a>В. Применение инструкции KILL для завершения потерянной распределенной транзакции  
 В следующем примере показано, как для завершения потерянной распределенной транзакции (код сеанса = -2) с *UOW* из `D5499C66-E398-45CA-BF7E-DC9C194B48CF`.  
  
```sql  
KILL 'D5499C66-E398-45CA-BF7E-DC9C194B48CF';  
```  

  
## <a name="see-also"></a>См. также:  
 [KILL STATS JOB &#40; Transact-SQL &#41;](../../t-sql/language-elements/kill-stats-job-transact-sql.md)   
 [KILL QUERY NOTIFICATION SUBSCRIPTION &#40; Transact-SQL &#41;](../../t-sql/language-elements/kill-query-notification-subscription-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Завершение работы &#40; Transact-SQL &#41;](../../t-sql/language-elements/shutdown-transact-sql.md)   
 [@@SPID &#40;Transact-SQL&#41;](../../t-sql/functions/spid-transact-sql.md)   
 [sys.dm_exec_requests &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_exec_sessions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_tran_locks &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)   
 [sp_lock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
  
  
