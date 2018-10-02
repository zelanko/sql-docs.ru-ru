---
title: KILL (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/31/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- KILL_TSQL
- KILL
dev_langs:
- TSQL
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
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d2eec14db312bb6fb2a8fb65bb51e396a4c1be3f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837006"
---
# <a name="kill-transact-sql"></a>KILL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Прерывает пользовательский процесс, определяемый идентификатором сеанса или единицей работы (UOW). Если для завершения процесса, указанного с помощью SPID или UOW, необходимо отменить большое количество операций, для выполнения инструкции KILL может понадобиться значительное время. Выполнение инструкции особенно затягивается при отмене длительной транзакции.  
  
 С помощью инструкции KILL можно завершить нормальное соединение, которое внутренне завершит транзакции, связанные с заданным идентификатором сеанса. Эту инструкцию также можно применять для завершения потерянных и сомнительных распределенных транзакций при использовании координатора распределенных транзакций [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MS DTC).  
  
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
 *session ID*  
 Идентификатор сеанса завершаемого процесса. *session ID* является уникальным целым числом (**int**), которое при подключении присваивается каждому соединению пользователя. Значение идентификатора сеанса остается привязанным к соединению в течение всего времени соединения. По окончании соединения данное целое значение освобождается и может быть присвоено другому соединению.  
Следующий запрос может помочь выявить `session_id`, который требуется удалить:  
 ```sql  
 SELECT conn.session_id, host_name, program_name,
     nt_domain, login_name, connect_time, last_request_end_time 
FROM sys.dm_exec_sessions AS sess
JOIN sys.dm_exec_connections AS conn
    ON sess.session_id = conn.session_id;
```  
  
*UOW*  
**Применимо к**: (с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).
  
 Задает идентификатор единицы работы (UOW) распределенных транзакций. *UOW* представляет собой идентификатор GUID, который можно получить из столбца request_owner_guid динамического административного представления sys.dm_tran_locks. *UOW* также может быть получен из журнала ошибок или из монитора транзакций MS DTC. Дополнительные сведения о наблюдении за распределенными транзакциями см. в руководстве пользователя MS DTC.  
  
 Используйте инструкцию KILL *UOW* для завершения потерянных распределенных транзакций. Эти транзакции не связаны с идентификаторами реальных сеансов, но искусственно связаны с идентификатором сеанса -2. Этот идентификатор упрощает поиск потерянных транзакций с помощью запроса столбца идентификатора сеанса из динамических административных представлений sys.dm_tran_locks, sys.dm_exec_sessions или sys.dm_exec_requests.  
  
 WITH STATUSONLY  
 Создает отчет о состоянии для конкретного *session ID* или *UOW*, который выполняет откат из-за выполненной ранее инструкции KILL. Инструкция KILL WITH STATUSONLY не завершает и не откатывает *session ID* или *UOW*. Команда только отображает текущее состояние отката.  
  
## <a name="remarks"></a>Remarks  
 Инструкция KILL обычно используется для прерывания процессов, блокирующих другие важные процессы или выполняющих запросы, занимающие необходимые системные ресурсы. Системные процессы и процессы, выполняющие расширенные хранимые процедуры, не могут быть прерваны.  
  
 Инструкцию KILL необходимо использовать осторожно, особенно при выполнении критических процессов. Существует опасность прерывания собственного процесса. Не нужно прерывать следующие процессы:  
  
-   AWAITING COMMAND  
-   CHECKPOINT SLEEP  
-   LAZY WRITER  
-   LOCK MONITOR;  
-   SIGNAL HANDLER  
  
Аргумент @@SPID позволяет отобразить идентификатор текущего сеанса.  
  
 Чтобы получить отчет о значениях идентификаторов активных сеансов, можно запросить столбец session_id из динамических административных представлений sys.dm_tran_locks, sys.dm_exec_sessions и sys.dm_exec_requests. Также можно посмотреть столбец SPID, возвращаемый системной хранимой процедурой sp_who. Если откат выполняется для конкретного SPID, столбец cmd результирующего набора процедуры sp_who для этого SPID будет содержать значение KILLED/ROLLBACK.  
  
 Если какое-либо соединение имеет блокировку на ресурс базы данных и блокирует обработку остальных соединений, идентификаторы сеансов заблокированных соединений появятся в столбце `blocking_session_id` представления `sys.dm_exec_requests` или в столбце `blk`, возвращенном хранимой процедурой `sp_who`.  
  
 Инструкцию KILL можно применять для решения проблем с сомнительными распределенными транзакциями. Эти транзакции представляют собой неразрешимые распределенные транзакции, возникшие в результате незапланированных повторных стартов сервера баз данных или координатора MS DTC. Дополнительные сведения о сомнительных транзакциях см. в разделе "Двухфазная фиксация" в статье [Использование помеченных транзакций для согласованного восстановления связанных баз данных (модель полного восстановления)](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
## <a name="using-with-statusonly"></a>Использование предложения WITH STATUSONLY  
 Инструкция KILL WITH STATUSONLY создает отчет только в том случае, если в сеансе или UOW выполняется откат, вызванный введенной ранее инструкцией KILL *session ID*|*UOW*. Отчет о состоянии отображает процесс выполнения отката (в процентах), а также выводит ожидаемое время до окончания операции (в секундах) в следующей форме:  
  
 `Spid|UOW <xxx>: Transaction rollback in progress. Estimated rollback completion: <yy>% Estimated time left: <zz> seconds`  
  
 Если откат session ID или UOW к моменту выполнения инструкции KILL *session ID*|*UOW* WITH STATUSONLY уже завершен либо процедура отката в данный момент не выполняется, выполнение инструкции KILL *session ID*|*UOW* WITH STATUSONLY возвращает следующую ошибку:  
  
 ```
"Msg 6120, Level 16, State 1, Line 1"  
"Status report cannot be obtained. Rollback operation for Process ID <session ID> is not in progress."
```  
  
 Аналогичный отчет о состоянии может быть получен при повторном выполнении инструкции KILL *session ID*|*UOW* без использования параметра WITH STATUSONLY, однако делать это не рекомендуется. Повторный вызов инструкции KILL *session ID* может вызвать завершение нового процесса в случае, если процесс отката был завершен, а значение идентификатора сеанса было присвоено другой задаче до запуска новой инструкции KILL. Указание параметра WITH STATUSONLY предотвращает указанные последствия.  
  
## <a name="permissions"></a>Разрешения  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:** необходимо разрешение ALTER ANY CONNECTION. Разрешение ALTER ANY CONNECTION включено с членством в предопределенных ролях сервера sysadmin или processadmin.  
  
 **[!INCLUDE[ssSDS](../../includes/sssds-md.md)]:** необходимо разрешение KILL DATABASE CONNECTION. Имя входа субъекта серверного уровня имеет разрешение KILL DATABASE CONNECTION.  
  
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
 Следующий пример показывает, как завершить потерянную распределенную транзакцию (идентификатор сеанса = –2) с *UOW*, равным `D5499C66-E398-45CA-BF7E-DC9C194B48CF`.  
  
```sql  
KILL 'D5499C66-E398-45CA-BF7E-DC9C194B48CF';  
```  

  
## <a name="see-also"></a>См. также:  
 [KILL STATS JOB (Transact-SQL)](../../t-sql/language-elements/kill-stats-job-transact-sql.md)   
 [KILL QUERY NOTIFICATION SUBSCRIPTION (Transact-SQL)](../../t-sql/language-elements/kill-query-notification-subscription-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [SHUTDOWN (Transact-SQL)](../../t-sql/language-elements/shutdown-transact-sql.md)   
 [@@SPID (Transact-SQL)](../../t-sql/functions/spid-transact-sql.md)   
 [sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_exec_sessions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_tran_locks (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)   
 [sp_lock (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
  
  
