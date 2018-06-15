---
title: sys.dm_exec_requests (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_requests_TSQL
- sys.dm_exec_requests
- dm_exec_requests_TSQL
- dm_exec_requests
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_requests dynamic management view
ms.assetid: 4161dc57-f3e7-4492-8972-8cfb77b29643
caps.latest.revision: 67
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1b8e51c1078ebe9b1fd2784a14e8c8e1575eae27
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34467960"
---
# <a name="sysdmexecrequests-transact-sql"></a>sys.dm_exec_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о каждом из запросов, выполняющихся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Чтобы выполнить код, внешний по отношению к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например, расширенную хранимую процедуру или распределенный запрос), поток должен выйти из-под управления планировщика, работающего в режиме без вытеснения. Для этого исполнитель переходит в режим с вытеснением. Значения времени, возвращаемые этим динамическим административным представлением, не включают время, затраченное в режиме с вытеснением.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|Идентификатор сеанса, к которому относится данный запрос. Не допускает значение NULL.|  
|request_id|**int**|Идентификатор запроса. Уникален в контексте сеанса. Не допускает значение NULL.|  
|start_time|**datetime**|Метка времени поступления запроса. Не допускает значение NULL.|  
|status|**nvarchar(30)**|Состояние запроса. Может иметь одно из следующих значений.<br /><br /> Историческая справка<br />Запущен<br />Готово к запуску<br />В режиме ожидания<br />Приостановлена<br /><br /> Не допускает значение NULL.|  
|command|**nvarchar(32)**|Тип выполняемой в данный момент команды. Основные типы команд:<br /><br /> SELECT<br />INSERT<br />UPDATE<br />DELETE<br />BACKUP LOG<br />BACKUP DATABASE<br />DBCC<br />FOR<br /><br /> Текст запроса можно получить при помощи функции sys.dm_exec_sql_text, передав ей значение столбца sql_handle. Внутренние системные процессы устанавливают команду в соответствии с выполняемой задачей. Например:<br /><br /> LOCK MONITOR;<br />CHECKPOINTLAZY;<br />WRITER.<br /><br /> Не допускает значение NULL.|  
|sql_handle|**varbinary(64)**|Хэш-карта текста SQL-запроса. Допускает значение NULL.|  
|statement_start_offset|**int**|Количество символов в выполняемом в настоящий момент пакете или хранимой процедуре, в которой запущена текущая инструкция. Может применяться вместе с функциями динамического управления sql_handle, statement_end_offset и sys.dm_exec_sql_text для извлечения исполняемой в настоящий момент инструкции по запросу. Допускает значение NULL.|  
|statement_end_offset|**int**|Количество символов в выполняемом в настоящий момент пакете или хранимой процедуре, в которой завершилась текущая инструкция. Может применяться вместе с функциями динамического управления sql_handle, statement_end_offset и sys.dm_exec_sql_text для извлечения исполняемой в настоящий момент инструкции по запросу. Допускает значение NULL.|  
|plan_handle|**varbinary(64)**|Хэш-карта плана выполнения SQL. Допускает значение NULL.|  
|database_id|**smallint**|Идентификатор базы данных, к которой выполняется запрос. Не допускает значение NULL.|  
|user_id|**int**|Идентификатор пользователя, отправившего данный запрос. Не допускает значение NULL.|  
|connection_id|**uniqueidentifier**|Идентификатор соединения, по которому поступил запрос. Допускает значение NULL.|  
|blocking_session_id|**smallint**|Идентификатор сеанса, блокирующего данный запрос. Если этот столбец содержит значение NULL, то запрос не блокирован или сведения о сеансе блокировки недоступны (или не могут быть идентифицированы).<br /><br /> -2 = Блокирующий ресурс принадлежит потерянной распределенной транзакции.<br /><br /> -3 = Блокирующий ресурс принадлежит отложенной транзакции восстановления.<br /><br /> -4 = Идентификатор сеанса владельца кратковременной блокировки определить на данный момент не удалось из-за переходов между внутренними состояниями кратковременной блокировки.|  
|wait_type|**nvarchar(60)**|Если запрос в настоящий момент блокирован, в столбце содержится тип ожидания. Допускает значение NULL.<br /><br /> Сведения о типах ожиданий см. в разделе [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|  
|wait_time|**int**|Если запрос в настоящий момент блокирован, в столбце содержится продолжительность текущего ожидания (в миллисекундах). Не допускает значение NULL.|  
|last_wait_type|**nvarchar(60)**|Если запрос был блокирован ранее, в столбце содержится тип последнего ожидания. Не допускает значение NULL.|  
|wait_resource|**nvarchar(256)**|Если запрос в настоящий момент блокирован, в столбце указан ресурс, освобождения которого ожидает запрос. Не допускает значение NULL.|  
|open_transaction_count|**int**|Число транзакций, открытых для данного запроса. Не допускает значение NULL.|  
|open_resultset_count|**int**|Число результирующих наборов, открытых для данного запроса. Не допускает значение NULL.|  
|transaction_id|**bigint**|Идентификатор транзакции, в которой выполняется запрос. Не допускает значение NULL.|  
|context_info|**varbinary(128)**|Значение CONTEXT_INFO сеанса. Допускает значение NULL.|  
|percent_complete|**real**|Процент завершения работы для следующих команд.<br /><br /> ALTER INDEX REORGANIZE<br />параметра AUTO_SHRINK с ALTER DATABASE<br />BACKUP DATABASE<br />DBCC CHECKDB<br />DBCC CHECKFILEGROUP<br />DBCC CHECKTABLE<br />DBCC INDEXDEFRAG<br />DBCC SHRINKDATABASE<br />DBCC SHRINKFILE<br />RECOVERY<br />RESTORE DATABASE<br />ROLLBACK<br />TDE ENCRYPTION<br /><br /> Не допускает значение NULL.|  
|estimated_completion_time|**bigint**|Только для внутреннего использования. Не допускает значение NULL.|  
|cpu_time|**int**|Время ЦП (в миллисекундах), затраченное на выполнение запроса. Не допускает значение NULL.|  
|total_elapsed_time|**int**|Общее время, истекшее с момента поступления запроса (в миллисекундах). Не допускает значение NULL.|  
|scheduler_id|**int**|Идентификатор планировщика, который планирует данный запрос. Не допускает значение NULL.|  
|task_address|**varbinary(8)**|Адрес блока памяти, выделенного для задачи, связанной с этим запросом. Допускает значение NULL.|  
|reads|**bigint**|Число операций чтения, выполненных данным запросом. Не допускает значение NULL.|  
|writes|**bigint**|Число операций записи, выполненных данным запросом. Не допускает значение NULL.|  
|logical_reads|**bigint**|Число логических операций чтения, выполненных данным запросом. Не допускает значение NULL.|  
|text_size|**int**|Установка параметра TEXTSIZE для данного запроса. Не допускает значение NULL.|  
|language|**nvarchar(128)**|Установка языка для данного запроса. Допускает значение NULL.|  
|date_format|**nvarchar(3)**|Установка параметра DATEFORMAT для данного запроса. Допускает значение NULL.|  
|date_first|**smallint**|Установка параметра DATEFIRST для данного запроса. Не допускает значение NULL.|  
|quoted_identifier|**бит**|1 = Параметр QUOTED_IDENTIFIER для запроса включен (ON). В противном случае — 0.<br /><br /> Не допускает значение NULL.|  
|arithabort|**бит**|1 = Параметр ARITHABORT для запроса включен (ON). В противном случае — 0.<br /><br /> Не допускает значение NULL.|  
|ansi_null_dflt_on|**бит**|1 = Параметр ANSI_NULL_DFLT_ON для запроса включен (ON). В противном случае — 0.<br /><br /> Не допускает значение NULL.|  
|ansi_defaults|**бит**|1 = Параметр ANSI_DEFAULTS для запроса включен (ON). В противном случае — 0.<br /><br /> Не допускает значение NULL.|  
|ansi_warnings|**бит**|1 = Параметр ANSI_WARNINGS для запроса включен (ON). В противном случае — 0.<br /><br /> Не допускает значение NULL.|  
|ansi_padding|**бит**|1 = Параметр ANSI_PADDING для запроса включен (ON).<br /><br /> В противном случае — 0.<br /><br /> Не допускает значение NULL.|  
|ansi_nulls|**бит**|1 = Параметр ANSI_NULLS для запроса включен (ON). В противном случае — 0.<br /><br /> Не допускает значение NULL.|  
|concat_null_yields_null|**бит**|1 = Параметр CONCAT_NULL_YIELDS_NULL для запроса включен (ON). В противном случае — 0.<br /><br /> Не допускает значение NULL.|  
|transaction_isolation_level|**smallint**|Уровень изоляции, с которым создана транзакция для данного запроса. Не допускает значение NULL.<br /><br /> 0 = не указан;<br /><br /> 1 = читать незафиксированные;<br /><br /> 2 = читать зафиксированные;<br /><br /> 3 = повторяемые результаты;<br /><br /> 4 = сериализуемые;<br /><br /> 5 = моментальный снимок.|  
|lock_timeout|**int**|Время ожидания блокировки для данного запроса (в миллисекундах). Не допускает значение NULL.|  
|deadlock_priority|**int**|Значение параметра DEADLOCK_PRIORITY для данного запроса. Не допускает значение NULL.|  
|row_count|**bigint**|Число строк, возвращенных клиенту по данному запросу. Не допускает значение NULL.|  
|prev_error|**int**|Последняя ошибка, происшедшая при выполнении запроса. Не допускает значение NULL.|  
|nest_level|**int**|Текущий уровень вложенности кода, выполняемого для данного запроса. Не допускает значение NULL.|  
|granted_query_memory|**int**|Число страниц, выделенных для выполнения поступившего запроса. Не допускает значение NULL.|  
|executing_managed_code|**бит**|Указывает, выполняет ли данный запрос в настоящее время код объекта среды CLR (например, процедуры, типа или триггера). Этот флаг установлен в течение всего времени, когда объект среды CLR находится в стеке, даже когда из среды вызывается код [!INCLUDE[tsql](../../includes/tsql-md.md)]. Не допускает значение NULL.|  
|group_id|**int**|Идентификатор группы рабочей нагрузки, которой принадлежит этот запрос. Не допускает значение NULL.|  
|query_hash|**binary(8)**|Двоичное хэш-значение рассчитывается для запроса и используется для идентификации запросов с аналогичной логикой. Можно использовать хэш запроса для определения использования статистических ресурсов для запросов, которые отличаются только своими литеральными значениями.|  
|query_plan_hash|**binary(8)**|Двоичное хэш-значение рассчитывается для плана выполнения запроса и используется для идентификации аналогичных планов выполнения запросов. Можно использовать хэш плана запроса для нахождения совокупной стоимости запросов со схожими планами выполнения.|  
|statement_sql_handle|**varbinary(64)**|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Дескриптор SQL для отдельного запроса. |  
|statement_context_id|**bigint**|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Необязательный внешний ключ к sys.query_context_settings. |  
|dop |**int** |**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Степень параллелизма запроса. |  
|parallel_worker_count |**int** |**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Количество зарезервированных параллельных рабочих процессов в случае параллельных запросов.  |  
|external_script_request_id |**uniqueidentifier** |**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Идентификатор запроса внешних скриптов, связанные с текущим запросом. |  
|is_resumable |**бит** |**Область применения**: начиная с [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает, является ли запрос возобновляемые индекса. |  
  
## <a name="permissions"></a>Разрешения  
 Если у пользователя есть `VIEW SERVER STATE` разрешение на сервере, пользователь увидит все выполняющиеся сеансы на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; в противном случае пользователь увидит только текущий сеанс. `VIEW SERVER STATE` не может быть предоставлено в [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] , `sys.dm_exec_requests` всегда ограничен до текущего соединения. 
  
## <a name="examples"></a>Примеры  
  
### <a name="a-finding-the-query-text-for-a-running-batch"></a>A. Поиск текста запроса для выполнения пакета  
 В следующем примере выполняется запрос `sys.dm_exec_requests` для поиска необходимого запроса и из его результата копируется `sql_handle`.  
  
```  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 Затем для получения текста инструкции используйте скопированный `sql_handle` с помощью системной функции `sys.dm_exec_sql_text(sql_handle)`.  
  
```  
SELECT * FROM sys.dm_exec_sql_text(< copied sql_handle >);  
GO  
```  
  
### <a name="b-finding-all-locks-that-a-running-batch-is-holding"></a>Б. Поиск всех блокировок, которые содержит выполняемый пакет  
 В следующем примере запрос **sys.dm_exec_requests** для поиска необходимого пакета и копируется его `transaction_id` из выходных данных.  
  
```  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 Нажмите, чтобы найти сведения о блокировке, используйте скопированный `transaction_id` с помощью системной функции **sys.dm_tran_locks**.  
  
```  
SELECT * FROM sys.dm_tran_locks   
WHERE request_owner_type = N'TRANSACTION'   
    AND request_owner_id = < copied transaction_id >;  
GO  
```  
  
### <a name="c-finding-all-currently-blocked-requests"></a>В. Поиск всех запросов, заблокированных в настоящий момент  
 В следующем примере запрос **sys.dm_exec_requests** для поиска сведений о заблокированных запросах.  
  
```  
SELECT session_id ,status ,blocking_session_id  
    ,wait_type ,wait_time ,wait_resource   
    ,transaction_id   
FROM sys.dm_exec_requests   
WHERE status = N'suspended';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)   
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_exec_query_memory_grants &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)   
 [sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)  
