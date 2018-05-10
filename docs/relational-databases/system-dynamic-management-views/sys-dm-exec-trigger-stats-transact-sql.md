---
title: sys.dm_exec_trigger_stats (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/10/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_trigger_stats
- dm_exec_trigger_stats_TSQL
- sys.dm_exec_trigger_stats_TSQL
- sys.dm_exec_trigger_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_trigger_stats dynamic management function
ms.assetid: 863498b4-849c-434d-b748-837411458738
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9b34f8c8d8dcdc98bdb49418ecf9b466e1068843
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmexectriggerstats-transact-sql"></a>sys.dm_exec_trigger_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает суммарную статистику производительности для кэшированных триггеров. Представление содержит одну строку для каждого триггера, а время существования строки равно времени пребывания триггера в кэше. Когда триггер удаляется из кэша, соответствующая строка исключается из данного представления. В этот момент возникает аналогично события трассировки SQL статистики производительности **sys.dm_exec_query_stats**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, в которой располагается триггер.|  
|**object_id**|**int**|Идентификатор триггера.|  
|**type**|**char(2)**|Тип объекта:<br /><br /> TA = триггер сборки (среда CLR)<br /><br /> TR = триггер SQL|  
|**Type_desc**|**nvarchar(60)**|Описание типа объекта:<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**sql_handle**|**varbinary(64)**|Это может использоваться для корреляции с запросами в **sys.dm_exec_query_stats** , которые выполнялись из этого триггера.|  
|**plan_handle**|**varbinary(64)**|Идентификатор плана в оперативной памяти. Этот идентификатор является временным и константным, только пока план сохраняется в кэше. Это значение может использоваться с **sys.dm_exec_cached_plans** динамическое административное представление.|  
|**cached_time**|**datetime**|Время, когда триггер был добавлен в кэш.|  
|**last_execution_time**|**datetime**|Время последнего выполнения триггера.|  
|**execution_count**|**bigint**|Количество выполненных триггера с момента последней компиляции.|  
|**total_worker_time**|**bigint**|Общее количество времени ЦП, в микросекундах, затраченного на выполнение триггера с момента его компиляции.|  
|**last_worker_time**|**bigint**|Время ЦП, затраченное на последнее выполнение триггера, в микросекундах.|  
|**min_worker_time**|**bigint**|Максимальное время ЦП в микросекундах, которое этот триггер когда-либо тратил за одно выполнение.|  
|**max_worker_time**|**bigint**|Максимальное время ЦП в микросекундах, которое этот триггер когда-либо тратил за одно выполнение.|  
|**total_physical_reads**|**bigint**|Общее количество физического считывания при выполнении триггера с момента его компиляции.|  
|**last_physical_reads**|**bigint**|Число физических операций чтения, выполненных последнего выполнения триггера.|  
|**min_physical_reads**|**bigint**|Минимальное количество операций физического считывания этот триггер когда-либо выполняли за одно выполнение.|  
|**max_physical_reads**|**bigint**|Максимальное количество операций физического считывания этот триггер когда-либо выполняли за одно выполнение.|  
|**total_logical_writes**|**bigint**|Общее количество операций логической записи при выполнении триггера с момента его компиляции.|  
|**last_logical_writes**|**bigint**|Количество операций логической записи выполняется последнего выполнения триггера.|  
|**min_logical_writes**|**bigint**|Минимальное количество операций логической записи, которые этот триггер когда-либо выполняли за одно выполнение.|  
|**max_logical_writes**|**bigint**|Максимальное количество операций логической записи, которые этот триггер когда-либо выполняли за одно выполнение.|  
|**total_logical_reads**|**bigint**|Общее число логического считывания при выполнении триггера с момента его компиляции.|  
|**last_logical_reads**|**bigint**|Число логических операций чтения, выполненных последнего выполнения триггера.|  
|**min_logical_reads**|**bigint**|Минимальное количество операций логического считывания этот триггер когда-либо выполняли за одно выполнение.|  
|**max_logical_reads**|**bigint**|Максимальное количество операций логического считывания этот триггер когда-либо выполняли за одно выполнение.|  
|**total_elapsed_time**|**bigint**|Общее затраченное время, в микросекундах, выполнение триггера.|  
|**last_elapsed_time**|**bigint**|Время, затраченное на последнее выполнение триггера, в микросекундах.|  
|**min_elapsed_time**|**bigint**|Минимальное затраченное время в микросекундах завершить выполнение триггера.|  
|**max_elapsed_time**|**bigint**|Максимальное время, в микросекундах, выполнение триггера.| 
|**total_spills**|**bigint**|Общее количество страниц, записанных при выполнении триггера с момента его компиляции.<br /><br /> **Применяется к**: начиная с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**last_spills**|**bigint**|Количество страниц, сброшенных последнего выполнения триггера.<br /><br /> **Применяется к**: начиная с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**min_spills**|**bigint**|Минимальное количество страниц, которые этот триггер когда-либо сброшенных за одно выполнение.<br /><br /> **Применяется к**: начиная с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**max_spills**|**bigint**|Максимальное число страниц, которые этот триггер когда-либо сброшенных за одно выполнение.<br /><br /> **Применяется к**: начиная с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
  
## <a name="remarks"></a>Замечания  
 Динамические административные представления в среде [!INCLUDE[ssSDS](../../includes/sssds-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Чтобы избежать предоставления этих сведений, все строки, содержащие данные, не принадлежащие к подключенному клиенту, фильтруются.  

Статистика в представлении обновляется после завершения выполнения запроса.  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения о пяти первых триггерах, идентифицируемых по среднему затраченному времени.  
  
```sql  
SELECT TOP 5 d.object_id, d.database_id, DB_NAME(database_id) AS 'database_name',   
    OBJECT_NAME(object_id, database_id) AS 'trigger_name', d.cached_time,  
    d.last_execution_time, d.total_elapsed_time,   
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],   
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_trigger_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>См. также  
[Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
[sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
[sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)   
[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
  
