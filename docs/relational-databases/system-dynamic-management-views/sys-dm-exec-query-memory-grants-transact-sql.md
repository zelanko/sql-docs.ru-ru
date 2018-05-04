---
title: sys.dm_exec_query_memory_grants (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_query_memory_grants_TSQL
- sys.dm_exec_query_memory_grants
- sys.dm_exec_query_memory_grants_TSQL
- dm_exec_query_memory_grants
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_memory_grants dynamic management view
ms.assetid: 2c417747-2edd-4e0d-8a9c-e5f445985c1a
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1147bf6ebd4683a51bb2fed95cdddb2370cc843d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexecquerymemorygrants-transact-sql"></a>sys.dm_exec_query_memory_grants (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения обо всех запросах, которые запросили и ожидающих предоставления памяти или был предоставлен предоставления памяти. В этом представлении не будут отображены запросы, которые не нуждаются в предоставлении памяти. Например, для сортировки и операции хэш-соединения имеют выделения памяти для выполнения запроса во время запросов без **ORDER BY** предложение не будет иметь предоставления памяти.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Чтобы избежать предоставления этих сведений, все строки, содержащие данные, не принадлежащие к подключенному клиенту, фильтруются. Кроме того, значения в столбцах **scheduler_id**, **wait_order**, **pool_id**, **group_id** фильтруются; задайте значение столбца значение NULL.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_exec_query_memory_grants**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|Идентификатор (SPID) сеанса, в котором выполняется данный запрос.|  
|**request_id**|**int**|Идентификатор запроса. Уникален в контексте сеанса.|  
|**scheduler_id**|**int**|Идентификатор планировщика, который планирует данный запрос.|  
|**DoP**|**smallint**|Степень параллелизма данного запроса.|  
|**request_time**|**datetime**|Дата и время обращения запроса за предоставлением памяти.|  
|**grant_time**|**datetime**|Дата и время, когда запросу была предоставлена память. Возвращает значение NULL, если память еще не была предоставлена.|  
|**requested_memory_kb**|**bigint**|Общий объем запрошенной памяти в килобайтах.|  
|**granted_memory_kb**|**bigint**|Общий объем фактически предоставленной памяти в килобайтах. Может быть значение NULL, если память еще не была предоставлена. Типичные ситуации, это значение должно быть таким же, как **requested_memory_kb**. Для создания индекса сервер может разрешить дополнительное предоставление по требованию памяти, объем которой выходит за рамки изначально предоставленной памяти.|  
|**required_memory_kb**|**bigint**|Минимальный объем памяти в килобайтах (КБ), необходимый для выполнения данного запроса. **requested_memory_kb** соответствует или превышает это значение.|  
|**used_memory_kb**|**bigint**|Используемый в данный момент объем физической памяти (в килобайтах).|  
|**max_used_memory_kb**|**bigint**|Максимальный объем используемой до данного момента физической памяти в килобайтах.|  
|**query_cost**|**float**|Ожидаемая стоимость запроса.|  
|**timeout_sec**|**int**|Время ожидания данного запроса в секундах до отказа от обращения за предоставлением памяти.|  
|**resource_semaphore_id**|**smallint**|Неуникальный идентификатор семафора ресурса, которого ожидает данный запрос.<br /><br /> **Примечание:** этот идентификатор уникален в версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]. Данное изменение может повлиять на устранение проблем в запросах. Дополнительные сведения см. в подразделе «Замечания» далее в этом разделе.|  
|**queue_id**|**smallint**|Идентификатор ожидающей очереди, в которой данный запрос ожидает предоставления памяти. Значение NULL, если память уже предоставлена.|  
|**wait_order**|**int**|Последовательный порядок ожидающих запросов в указанной **queue_id**. Это значение может изменяться для заданного запроса, если другие запросы отказываются от предоставления памяти или получают ее. Значение NULL, если память уже предоставлена.|  
|**is_next_candidate**|**бит**|Является следующим кандидатом на предоставление памяти.<br /><br /> 1 = да<br /><br /> 0 = нет<br /><br /> NULL = память уже предоставлена.|  
|**wait_time_ms**|**bigint**|Время ожидания в миллисекундах. Значение NULL, если память уже предоставлена.|  
|**plan_handle**|**varbinary(64)**|Идентификатор для данного плана запроса. Используйте **sys.dm_exec_query_plan** чтобы извлечь фактический план XML.|  
|**sql_handle**|**varbinary(64)**|Идентификатор текста [!INCLUDE[tsql](../../includes/tsql-md.md)] для данного запроса. Используйте **sys.dm_exec_sql_text** Чтобы получить фактический [!INCLUDE[tsql](../../includes/tsql-md.md)] текста.|  
|**group_id**|**int**|Идентификатор группы рабочей нагрузки, в которой выполняется данный запрос.|  
|**pool_id**|**int**|Идентификатор пула ресурсов, к которому принадлежит данная группа рабочей нагрузки.|  
|**is_small**|**tinyint**|Значение 1 означает, что для данной операции предоставления памяти используется малый семафор ресурса. Значение 0 означает использование обычного семафора.|  
|**ideal_memory_kb**|**bigint**|Объем, в килобайтах (КБ), предоставленной памяти, необходимый для размещения всех данных в физической памяти. Основывается на оценке количества элементов.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
   
## <a name="remarks"></a>Замечания  
 Обычный сценарий отладки для времени ожидания запроса может выглядеть следующим образом:  
  
-   Проверьте общую системной памяти состояния с помощью [sys.dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md), [sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)и различных счетчиков производительности.  
  
-   Проверьте резервирование памяти выполнения запроса в **sys.dm_os_memory_clerks** где `type = 'MEMORYCLERK_SQLQERESERVATIONS'`.  
  
-   Проверьте запросы, ожидающие предоставления памяти с помощью **sys.dm_exec_query_memory_grants**.  
  
    ```  
    --Find all queries waiting in the memory queue  
    SELECT * FROM sys.dm_exec_query_memory_grants where grant_time is null  
    ```  
  
-   Поиск кэша для запросов с помощью выделения памяти[sys.dm_exec_cached_plans &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md) и [sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)  
  
    ```  
    -- retrieve every query plan from the plan cache  
    USE master;  
    GO  
    SELECT * FROM sys.dm_exec_cached_plans cp CROSS APPLY sys.dm_exec_query_plan(cp.plan_handle);  
    GO  
  
    ```  
  
-   Дополнительно изучите требующие много памяти запросы с помощью [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).  
  
    ```  
    --Find top 5 queries by average CPU time  
    SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
    Plan_handle, query_plan   
    FROM sys.dm_exec_query_stats AS qs  
    CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle)  
    ORDER BY total_worker_time/execution_count DESC;  
    GO  
  
    ```  
  
-   Если неконтролируемый запрос подозрителен, изучите план выполнения из [sys.dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md) и текст пакета из [sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md).  
  
 Запросы, использующие динамические административные представления и содержащие предложение ORDER BY или статистические функции, могут увеличить потребление памяти и таким образом усугубить проблему, которую призваны устранить.  
  
 Регулятор ресурсов позволяет администратору базы данных распределять ресурсы сервера между пулами ресурсов, используя до 64 пулов. Начиная с версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], каждый пул ведет себя как небольшой независимый экземпляр сервера и требует двух семафоров. Число строк, возвращаемых из **sys.dm_exec_query_resource_semaphores** может быть до 20 раз, чем количество строк, возвращаемых в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="see-also"></a>См. также  
 [sys.dm_exec_query_resource_semaphores &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql.md)   
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


