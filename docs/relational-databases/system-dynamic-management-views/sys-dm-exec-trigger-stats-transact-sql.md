---
title: "sys.dm_exec_trigger_stats (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_exec_trigger_stats
- dm_exec_trigger_stats_TSQL
- sys.dm_exec_trigger_stats_TSQL
- sys.dm_exec_trigger_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_trigger_stats dynamic management function
ms.assetid: 863498b4-849c-434d-b748-837411458738
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 67c6d5765ee5259134f6d9985a88bf94768490cf
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexectriggerstats-transact-sql"></a>sys.dm_exec_trigger_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает суммарную статистику производительности для кэшированных триггеров. Представление содержит одну строку для каждого триггера, а время существования строки равно времени пребывания триггера в кэше. Когда триггер удаляется из кэша, соответствующая строка исключается из данного представления. В этот момент возникает аналогично события трассировки SQL статистики производительности **sys.dm_exec_query_stats**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, в которой располагается триггер.|  
|**object_id**|**int**|Идентификатор триггера.|  
|**type**|**char(2)**|Тип объекта:<br /><br /> TA = триггер сборки (среда CLR)<br /><br /> TR = триггер SQL|  
|**Type_desc**|**nvarchar(60)**|Описание типа объекта:<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**sql_handle**|**varbinary(64)**|Это может использоваться для корреляции с запросами в **sys.dm_exec_query_stats** , которые выполнялись из этого триггера.|  
|**plan_handle**|**varbinary(64)**|Идентификатор плана в оперативной памяти. Этот идентификатор является временным и константным, только пока план сохраняется в кэше. Это значение может использоваться с **sys.dm_exec_cached_plans** динамическое административное представление.|  
|**cached_time**|**datetime**|Время, когда триггер был добавлен в кэш.|  
|**last_execution_time**|**datetime**|Время последнего выполнения триггера.|  
|**execution_count**|**bigint**|Количество выполнений триггера с момента последней компиляции.|  
|**total_worker_time**|**bigint**|Общее время ЦП, затраченное на выполнение триггера с момента компиляции, в микросекундах.|  
|**last_worker_time**|**bigint**|Время ЦП, затраченное на последнее выполнение триггера, в микросекундах.|  
|**min_worker_time**|**bigint**|Максимальное время ЦП (в микросекундах), которое этот триггер когда-либо затрачивал за одно выполнение.|  
|**max_worker_time**|**bigint**|Максимальное время ЦП (в микросекундах), которое этот триггер когда-либо затрачивал за одно выполнение.|  
|**total_physical_reads**|**bigint**|Общее количество операций физического считывания при выполнении триггера с момента его компиляции.|  
|**last_physical_reads**|**bigint**|Количество операций физического считывания за время последнего выполнения триггера.|  
|**min_physical_reads**|**bigint**|Минимальное количество операций физического считывания за одно выполнение триггера.|  
|**max_physical_reads**|**bigint**|Максимальное количество операций физического считывания за одно выполнение триггера.|  
|**total_logical_writes**|**bigint**|Общее количество операций логической записи при выполнении триггера с момента его компиляции.|  
|**last_logical_writes**|**bigint**|**total_physical_reads**число логических операций записи, выполненных время последнего выполнения триггера.|  
|**min_logical_writes**|**bigint**|Минимальное количество операций логической записи за одно выполнение триггера.|  
|**max_logical_writes**|**bigint**|Максимальное количество операций логической записи за одно выполнение триггера.|  
|**total_logical_reads**|**bigint**|Общее количество операций логического считывания при выполнении триггера с момента его компиляции.|  
|**last_logical_reads**|**bigint**|Количество операций логического считывания за время последнего выполнения триггера.|  
|**min_logical_reads**|**bigint**|Минимальное количество операций логического считывания за одно выполнение триггера.|  
|**max_logical_reads**|**bigint**|Максимальное количество операций логического считывания за одно выполнение триггера.|  
|**total_elapsed_time**|**bigint**|Общее время, затраченное на выполнение триггера, в микросекундах.|  
|**last_elapsed_time**|**bigint**|Время, затраченное на последнее выполнение триггера, в микросекундах.|  
|**min_elapsed_time**|**bigint**|Минимальное время, затраченное на одно выполнение триггера, в микросекундах.|  
|**max_elapsed_time**|**bigint**|Максимальное время, затраченное на одно выполнение триггера, в микросекундах.|  
  
## <a name="remarks"></a>Замечания  
 В базе данных SQL Windows Azure динамические административные представления не могут обеспечивать доступ к сведениям, которые влияют на включение базы данных, или к сведениям о других базах данных, к которым пользователь имеет доступ. Чтобы избежать предоставления этих сведений, все строки, содержащие данные, не принадлежащие к подключенному клиенту, фильтруются.  

Статистика в представлении обновляется после завершения выполнения запроса.  
  
## <a name="permissions"></a>Permissions  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.
  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения о пяти первых триггерах, идентифицируемых по среднему затраченному времени.  
  
```sql  
PRINT '--top 5 CPU consuming triggers '  
  
SELECT TOP 5 d.object_id, d.database_id, DB_NAME(database_id) AS 'database_name',   
    OBJECT_NAME(object_id, database_id) AS 'trigger_name', d.cached_time,  
    d.last_execution_time, d.total_elapsed_time,   
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],   
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_trigger_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>См. также:  
 [&#40; динамические административные представления и функции, связанные с выполнением Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sql_text &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
  [sys.dm_exec_procedure_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)   
 [sys.dm_exec_cached_plans &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
  
