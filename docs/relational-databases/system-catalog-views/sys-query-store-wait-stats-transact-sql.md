---
title: sys.query_store_wait_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 68ceb35ee3ef2cb3db3233c7050380584163c317
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067923"
---
# <a name="sysquerystorewaitstats-transact-sql"></a>sys.query_store_wait_stats (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Содержит сведения о ожидания для запроса.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**wait_stats_id**|**bigint**|Идентификатор строки, представляющее Статистика ожидания для plan_id, runtime_stats_interval_id, execution_type и wait_category. Он уникален только для последних интервалов статистики среды выполнения. Для интервала активной может быть несколько строк, представляющих статистику ожидания ссылается plan_id, с помощью выполнения тип, представленный execution_type и категории ожидания, представленное wait_category плана. Как правило, одна строка представляет статистику времени ожидания, в который записываются на диск, тогда как другие (s) представляют собой состояние в памяти. Таким образом Чтобы получить фактическое состояние для каждого интервала необходимо выполнять статистическое вычисление метрик, Группировка по plan_id, runtime_stats_interval_id, execution_type и wait_category. |  
|**plan_id**|**bigint**|Внешний ключ. Присоединяет к [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md).|  
|**runtime_stats_interval_id**|**bigint**|Внешний ключ. Присоединяет к [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md).|  
|**wait_category**|**tinyint**|Типы ожидания классифицируются по таблице, приведенной ниже, и затем время ожидания вычисляется по их категории ожидания. Разных категориях ожидания требуются разные обработки результатов анализа для устранения проблемы, но типы из одной категории интереса к сходные возможности по устранению неполадок ожидания и определение затронутого запроса в дополнение к ожиданий является то, что для завершения большинства подобные расследования успешно.|
|**wait_category_desc**|**nvarchar(128)**|Текстовое описание поля категории ожидания см. в следующей таблице.|
|**execution_type**|**tinyint**|Определяет тип выполнения запроса.<br /><br /> 0 — обычное выполнение (успешно завершено)<br /><br /> 3 - клиент прервал выполнение<br /><br /> 4 - исключение прервал выполнение|  
|**execution_type_desc**|**nvarchar(128)**|Текстовое описание выполнения тип поля:<br /><br /> 0 — обычный<br /><br /> 3 — прервано<br /><br /> 4 - исключение|  
|**total_query_wait_time_ms**|**bigint**|Общее `CPU wait` время для плана запроса в пределах интервала статистической обработки, и категория (указывается в миллисекундах) ожидания.|
|**avg_query_wait_time_ms**|**float**|Длительность для плана запроса на выполнение в категории статистической обработки интервала и ожидания (указывается в миллисекундах) ожидания среднее значение.|
|**last_query_wait_time_ms**|**bigint**|Последний длительность ожидания для плана запроса в пределах интервала статистической обработки и категория (указывается в миллисекундах) ожидания.|
|**min_query_wait_time_ms**|**bigint**|Минимум `CPU wait` время для плана запроса в пределах интервала статистической обработки, и категория (указывается в миллисекундах) ожидания.|
|**max_query_wait_time_ms**|**bigint**|Максимальное `CPU wait` время для плана запроса в пределах интервала статистической обработки, и категория (указывается в миллисекундах) ожидания.|
|**stdev_query_wait_time_ms**|**float**|`Query wait` стандартное отклонение длительности запроса план в пределах интервала статистической обработки и категория (указывается в миллисекундах) ожидания.|

## <a name="wait-categories-mapping-table"></a>Категории таблицы сопоставления ожидания

«%» используется в качестве подстановочного знака
  
|Целочисленное значение|Категория ожидания|Типы ожидания включить в категорию|  
|-----------------|---------------|-----------------|  
|**0**|**Unknown**|Неизвестно |  
|**1**|**CPU**|SOS_SCHEDULER_YIELD|
|**2**|**Рабочий поток**|THREADPOOL|
|**3**|**Блокировки**|LCK_M_%|
|**4**|**Кратковременной блокировки**|LATCH_ %|
|**5**|**Кратковременной блокировки буфера**|PAGELATCH_ %|
|**6**|**Буфер ввода-ВЫВОДА**|PAGEIOLATCH_ %|
|**7**|**Компиляция***|RESOURCE_SEMAPHORE_QUERY_COMPILE|
|**8**|**SQL CLR**|CLR %, SQLCLR %|
|**9**|**Зеркальное отображение**|DBMIRROR %|
|**10**|**Transaction**|XACT%, DTC%, TRAN_MARKLATCH_%, MSQL_XACT_%, TRANSACTION_MUTEX|
|**11**|**Простоя**|% SLEEP_, LAZYWRITER_SLEEP, SQLTRACE_BUFFER_FLUSH, SQLTRACE_INCREMENTAL_FLUSH_SLEEP, SQLTRACE_WAIT_ENTRIES, FT_IFTS_SCHEDULER_IDLE_WAIT, XE_DISPATCHER_WAIT, REQUEST_FOR_DEADLOCK_SEARCH, LOGMGR_QUEUE, ONDEMAND_TASK_QUEUE, CHECKPOINT_ ОЧЕРЕДИ, XE_TIMER_EVENT|
|**12**|**PreEmptive**|PREEMPTIVE_ %|
|**13**|**Компонент Service Broker**|BROKER_ % **(но не BROKER_RECEIVE_WAITFOR)**|
|**14**|**Ввод-ВЫВОД журнала TRAN**|LOGMGR, LOGBUFFER, LOGMGR_RESERVE_APPEND, LOGMGR_FLUSH, LOGMGR_PMM_LOG, CHKPT, WRITELOG|
|**15**|**Сетевого ввода-ВЫВОДА**|ASYNC_NETWORK_IO, NET_WAITFOR_PACKET, PROXY_NETWORK_IO, EXTERNAL_SCRIPT_NETWORK_IOF|
|**16**|**Parallelism**|ОЖИДАНИЯ CXPACKET, EXCHANGE|
|**17**|**Память**|RESOURCE_SEMAPHORE, CMEMTHREAD, CMEMPARTITIONED, EE_PMOLOCK, MEMORY_ALLOCATION_EXT, RESERVED_MEMORY_ALLOCATION_EXT, MEMORY_GRANT_UPDATE|
|**18**|**Посетитель ждать**|WAITFOR, WAIT_FOR_RESULTS, BROKER_RECEIVE_WAITFOR|
|**19**|**Трассировка**|TRACEWRITE, SQLTRACE_LOCK, SQLTRACE_FILE_BUFFER, SQLTRACE_FILE_WRITE_IO_COMPLETION, SQLTRACE_FILE_READ_IO_COMPLETION, SQLTRACE_PENDING_BUFFER_WRITERS, SQLTRACE_SHUTDOWN, QUERY_TRACEOUT, TRACE_EVTNOTIFF|
|**20**|**Полнотекстовый поиск**|FT_RESTART_CRAWL, FULLTEXT СБОРА ДАННЫХ, MSSEARCH, FT_METADATA_MUTEX, FT_IFTSHC_MUTEX, FT_IFTSISM_MUTEX, FT_IFTS_RWLOCK, FT_COMPROWSET_RWLOCK, FT_MASTER_MERGE, FT_PROPERTYLIST_CACHE, FT_MASTER_MERGE_COORDINATOR, PWAIT_RESOURCE_SEMAPHORE_FT_ PARALLEL_QUERY_SYNC|
|**21**|**Другие дискового ввода-ВЫВОДА**|ASYNC_IO_COMPLETION, IO_COMPLETION, BACKUPIO, WRITE_COMPLETION, IO_QUEUE_LIMIT, IO_RETRY|
|**22**|**Репликация**|SE_REPL_ %, REPL_ %, HADR_ % **(но не HADR_THROTTLE_LOG_RATE_GOVERNOR)** , % PWAIT_HADR_, REPLICA_WRITES, FCB_REPLICA_WRITE, FCB_REPLICA_READ, PWAIT_HADRSIM|
|**23**|**Скорость регулятора журналов**|LOG_RATE_GOVERNOR POOL_LOG_RATE_GOVERNOR, HADR_THROTTLE_LOG_RATE_GOVERNOR, INSTANCE_LOG_RATE_GOVERNOR|

**Компиляция** категории ожидания сейчас не поддерживается.

## <a name="permissions"></a>Разрешения

 Требуется разрешение `VIEW DATABASE STATE`.  
  
## <a name="see-also"></a>См. также

- [sys.database_query_store_options (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)
- [sys.query_context_settings (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)
- [sys.query_store_plan (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)
- [sys.query_store_query (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)
- [sys.query_store_query_text (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)
- [sys.query_store_runtime_stats_interval (Transact-SQL)](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)
- [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)
- [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)
- [Query Store хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
