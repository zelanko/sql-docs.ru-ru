---
title: sys.dm_exec_function_stats (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- sys.dm_exec_function_stats
- sys.dm_exec_function_stats_tsql
- dm_exec_function_stats
- dm_exec_function_stats_tsql
helpviewer_keywords:
- sys.dm_exec_function_stats dynamic management view
ms.assetid: 4c3d6a02-08e4-414b-90be-36b89a0e5a3a
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ad955c58adf7a77c1fab429657d2d8331602fb21
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmexecfunctionstats-transact-sql"></a>sys.dm_exec_function_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Возвращает суммарную статистику производительности для кэшированных функций. Представление возвращает по одной строке для каждого плана кэшированной функции, и время существования строки до тех пор, пока функция остается кэшируется. Когда функция удаляется из кэша, соответствующая строка исключается из данного представления. В этот момент возникает аналогично события трассировки SQL статистики производительности **sys.dm_exec_query_stats**. Возвращает сведения о скалярных функций, включая функции в памяти и скалярные функции CLR. Возвращает сведения о возвращающих табличное значение функций.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Чтобы избежать предоставления этих сведений, все строки, содержащие данные, не принадлежащие к подключенному клиенту, фильтруются.  
  
> [!NOTE]
> Начальный запрос представления **sys.dm_exec_function_stats** может выдавать неточные результаты, если на сервере выполняется рабочая нагрузка. Более точные результаты могут быть получены при повторном выполнении запроса.  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, в которой находится функция.|  
|**object_id**|**int**|Идентификационный номер объекта функции.|  
|**type**|**char(2)**|Тип объекта: FN = скалярные функции|  
|**type_desc**|**nvarchar(60)**|Описание типа объекта: SQL_SCALAR_FUNCTION|  
|**sql_handle**|**varbinary(64)**|Это может использоваться для корреляции с запросами в **sys.dm_exec_query_stats** , которые выполнялись из этой функции.|  
|**plan_handle**|**varbinary(64)**|Идентификатор плана в оперативной памяти. Этот идентификатор является временным и константным, только пока план сохраняется в кэше. Это значение может использоваться с **sys.dm_exec_cached_plans** динамическое административное представление.<br /><br /> Значение всегда равно 0x000 при использовании функции, скомпилированной таблицы запросов, оптимизированной для памяти.|  
|**cached_time**|**datetime**|Время, когда функции был добавлен в кэш.|  
|**last_execution_time**|**datetime**|Время последнего выполнения функции.|  
|**execution_count**|**bigint**|Количество выполненных функции с момента последней компиляции.|  
|**total_worker_time**|**bigint**|Общее время ЦП в микросекундах, при выполнении этой функции с момента его компиляции.<br /><br /> Для функций, скомпилированных в собственном коде **total_worker_time** может быть неточным, если меньше миллисекунды.|  
|**last_worker_time**|**bigint**|Время ЦП, в микросекундах, затраченное время последнего выполнения функции. <sup>1</sup>|  
|**min_worker_time**|**bigint**|Минимальное время ЦП в микросекундах, эта функция когда-либо тратил за одно выполнение. <sup>1</sup>|  
|**max_worker_time**|**bigint**|Максимальное время ЦП в микросекундах, эта функция когда-либо тратил за одно выполнение. <sup>1</sup>|  
|**total_physical_reads**|**bigint**|Общее количество операций физического считывания при выполнении этой функции с момента его компиляции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**last_physical_reads**|**bigint**|Количество операций физического считывания выполнить последнее время выполнения функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**min_physical_reads**|**bigint**|Минимальное число физических операций считывания эта функция за одно выполнение.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**max_physical_reads**|**bigint**|Максимальное число физических операций считывания эта функция за одно выполнение.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**total_logical_writes**|**bigint**|Общее количество операций логической записи при выполнении этой функции с момента его компиляции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**last_logical_writes**|**bigint**|Количество страниц в буферном пуле, загрязненных во время последнего выполнения плана. Если страница уже является «грязной» (т. е. измененной), операции записи не учитываются.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**min_logical_writes**|**bigint**|Минимальное количество операций логической записи, эта функция никогда не выполняется за одно выполнение.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**max_logical_writes**|**bigint**|Максимальное количество операций логической записи, эта функция никогда не выполняется за одно выполнение.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**total_logical_reads**|**bigint**|Общее количество операций логического считывания при выполнении этой функции с момента его компиляции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**last_logical_reads**|**bigint**|Количество операций логического считывания выполнить последнее время выполнения функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**min_logical_reads**|**bigint**|Минимальное число логических операций чтения, эта функция никогда не выполняется за одно выполнение.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**max_logical_reads**|**bigint**|Максимальное число логических операций чтения, эта функция никогда не выполняется за одно выполнение.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**total_elapsed_time**|**bigint**|Общее затраченное время в микросекундах, выполнение этой функции.|  
|**last_elapsed_time**|**bigint**|Затраченное время в микросекундах, последнее выполнение этой функции.|  
|**min_elapsed_time**|**bigint**|Минимальное затраченное время в микросекундах завершил выполнение этой функции.|  
|**max_elapsed_time**|**bigint**|Максимальное время, в микросекундах завершил выполнение этой функции.|  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает сведения о верхней десять функций, идентифицируемых по среднему затраченного времени.  
  
```  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'function name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_function_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 
 [sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)   
 [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  
  
  
