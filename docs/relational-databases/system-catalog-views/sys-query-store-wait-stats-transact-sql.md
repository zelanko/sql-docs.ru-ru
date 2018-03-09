---
title: "sys.query_store_wait_stats (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/21/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.query_store_wait_stats
- query_store_wait_stats
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_wait_stats catalog view
- sys.query_store_wait_stats catalog view
ms.assetid: ccf7a57c-314b-450c-bd34-70749a02784a
caps.latest.revision: 
author: AndrejsAnt
ms.author: AndrejsAnt
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3133014e12f52b58e3beacdc0ba09083c661ff63
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysquerystorewaitstats-transact-sql"></a>sys.query_store_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Содержит сведения о ожидания для запроса.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**wait_stats_id**|**bigint**|Строка, представляющая статистику ожидания для plan_id, runtime_stats_interval_id, execution_type и wait_category идентификатор. Он уникален только для последних интервалов статистики среды выполнения. Для активной интервала может быть несколько строк, представляющих статистики ожидания ссылается plan_id, с помощью представленных execution_type и категории ожидания, представленное wait_category тип выполнения плана. Как правило, одна строка представляет статистику ожидания, записываются на диск, в то время как другие (s) представляют состояние в памяти. Таким образом Чтобы получить фактическое состояние для каждого интервала необходимо статистические показатели, Группировка по plan_id, runtime_stats_interval_id, execution_type и wait_category. |  
|**plan_id**|**bigint**|Внешний ключ. Присоединяет к [sys.query_store_plan &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md).|  
|**runtime_stats_interval_id**|**bigint**|Внешний ключ. Присоединяет к [sys.query_store_runtime_stats_interval &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md).|  
|**wait_category**|**tinyint**|Типы ожидания подразделяются на следующей таблицы, а затем агрегируются время ожидания эти ожидания категорий. В разных категориях ожидания требуются разные виды последующего анализа для устранения проблемы, но типы ожидания из одной категории имеют очень схожие процедуры устранения неполадок. Определение затронутого запроса с наибольшим уровнем ожидания позволит успешно завершать подобные расследования.|
|**wait_category_desc**|**nvarchar(128)**|Текстовое описание поля категории ожидания см. в следующей таблице.|
|**execution_type**|**tinyint**|Определяет тип выполнения запроса.<br /><br /> 0 — регулярного выполнения (успешно завершено)<br /><br /> 3 — инициируется клиентом прервал выполнение<br /><br /> 4 - выполнение прервано исключение|  
|**execution_type_desc**|**nvarchar(128)**|Текстовое описание выполнения тип поля:<br /><br /> 0 — обычный<br /><br /> 3 — прервана<br /><br /> 4 - исключение|  
|**total_query_wait_time_ms**|**bigint**|Общее время ЦП, время ожидания для плана запроса в течение интервала статистических вычислений и категории (предупреждение в миллисекундах) ожидания.|
|**avg_query_wait_time_ms**|**float**|Среднее длительность ожидания для плана запроса на выполнение в категории статистической обработки интервала и ожидания (предупреждение в миллисекундах).|
|**last_query_wait_time_ms**|**bigint**|Последним длительность ожидания для плана запроса в течение интервала статистических вычислений и категории (предупреждение в миллисекундах) ожидания.|
|**min_query_wait_time_ms**|**bigint**|Минимальная пропускная способность ЦП, время ожидания для плана запроса в течение интервала статистических вычислений и категории (предупреждение в миллисекундах) ожидания.|
|**max_query_wait_time_ms**|**bigint**|Максимальная пропускная способность ЦП, время ожидания для плана запроса в течение интервала статистических вычислений и категории (предупреждение в миллисекундах) ожидания.|
|**stdev_query_wait_time_ms**|**float**|Запрос ожидания длительность стандартное отклонение для плана запроса в течение интервала статистических вычислений и категории (предупреждение в миллисекундах) ожидания.|

 ## <a name="wait-categories-mapping-table"></a>Категории таблицы сопоставления ожидания  
  *«%» используется в качестве подстановочного знака*
  
|Целочисленное значение|Категории ожидания|Включать типы ожиданий в категории|  
|-----------------|---------------|-----------------|  
|**0**|**Unknown**|Неизвестно |  
|**1**|**ЦП**|SOS_SCHEDULER_YIELD|
|**2**|**Рабочий поток**|THREADPOOL|
|**3**|**Lock**|LCK_M_%|
|**4**|**Latch**|LATCH_%|
|**5**|**Кратковременная блокировка буфера**|PAGELATCH_%|
|**6**|**Буфер ввода-ВЫВОДА**|PAGEIOLATCH_ %|
|**7**|**Компиляция***|RESOURCE_SEMAPHORE_QUERY_COMPILE|
|**8**|**SQL CLR**|CLR%, SQLCLR%|
|**9**|**Зеркальное отображение**|DBMIRROR%|
|**10**|**Transaction**|XACT%, DTC%, TRAN_MARKLATCH_%, MSQL_XACT_%, TRANSACTION_MUTEX|
|**11**|**Idle**|SLEEP_%, LAZYWRITER_SLEEP, SQLTRACE_BUFFER_FLUSH, SQLTRACE_INCREMENTAL_FLUSH_SLEEP, SQLTRACE_WAIT_ENTRIES, FT_IFTS_SCHEDULER_IDLE_WAIT, XE_DISPATCHER_WAIT, REQUEST_FOR_DEADLOCK_SEARCH, LOGMGR_QUEUE, ONDEMAND_TASK_QUEUE, CHECKPOINT_QUEUE, XE_TIMER_EVENT|
|**12**|**Preemptive**|PREEMPTIVE_ %|
|**13**|**Компонент Service Broker**|BROKER_ % **(но не BROKER_RECEIVE_WAITFOR)**|
|**14**|**Ввод-ВЫВОД журнала TRAN**|LOGMGR, LOGBUFFER, LOGMGR_RESERVE_APPEND, LOGMGR_FLUSH, LOGMGR_PMM_LOG, CHKPT, WRITELOGF|
|**15**|**Сетевого ввода-ВЫВОДА**|ASYNC_NETWORK_IO, NET_WAITFOR_PACKET, PROXY_NETWORK_IO, EXTERNAL_SCRIPT_NETWORK_IOF|
|**16**|**Parallelism**|CXPACKET EXCHANGE|
|**17**|**Память**|RESOURCE_SEMAPHORE, CMEMTHREAD, CMEMPARTITIONED, EE_PMOLOCK, MEMORY_ALLOCATION_EXT, RESERVED_MEMORY_ALLOCATION_EXT, MEMORY_GRANT_UPDATE|
|**18**|**Ожидание пользователя**|WAITFOR, WAIT_FOR_RESULTS, BROKER_RECEIVE_WAITFOR|
|**19**|**Трассировка**|TRACEWRITE, SQLTRACE_LOCK, SQLTRACE_FILE_BUFFER, SQLTRACE_FILE_WRITE_IO_COMPLETION, SQLTRACE_FILE_READ_IO_COMPLETION, SQLTRACE_PENDING_BUFFER_WRITERS, SQLTRACE_SHUTDOWN, QUERY_TRACEOUT, TRACE_EVTNOTIFF|
|**20**|**Полнотекстовый поиск**|FT_RESTART_CRAWL, FULLTEXT GATHERER, MSSEARCH, FT_METADATA_MUTEX, FT_IFTSHC_MUTEX, FT_IFTSISM_MUTEX, FT_IFTS_RWLOCK, FT_COMPROWSET_RWLOCK, FT_MASTER_MERGE, FT_PROPERTYLIST_CACHE, FT_MASTER_MERGE_COORDINATOR, PWAIT_RESOURCE_SEMAPHORE_FT_PARALLEL_QUERY_SYNC|
|**21**|**Другие дискового ввода-ВЫВОДА**|ASYNC_IO_COMPLETION, IO_COMPLETION, BACKUPIO, WRITE_COMPLETION, IO_QUEUE_LIMIT, IO_RETRY|
|**22**|**Репликация**|SE_REPL_ %, REPL_ %, HADR_ % **(но не HADR_THROTTLE_LOG_RATE_GOVERNOR)**, PWAIT_HADR_ %, REPLICA_WRITES, FCB_REPLICA_WRITE, FCB_REPLICA_READ, PWAIT_HADRSIM|
|**23**|**Частота регулятора журналов**|LOG_RATE_GOVERNOR POOL_LOG_RATE_GOVERNOR, HADR_THROTTLE_LOG_RATE_GOVERNOR, INSTANCE_LOG_RATE_GOVERNOR|

***Компиляция** категории ожидания в настоящее время не поддерживается. 

  
## <a name="permissions"></a>Разрешения  
 Требуется **VIEW DATABASE STATE** разрешение.  
  
## <a name="see-also"></a>См. также  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Хранимые процедуры &#40; в хранилище запросов Transact-SQL &#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
