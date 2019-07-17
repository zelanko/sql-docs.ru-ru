---
title: sys.dm_exec_function_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/30/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_function_stats
- sys.dm_exec_function_stats_tsql
- dm_exec_function_stats
- dm_exec_function_stats_tsql
helpviewer_keywords:
- sys.dm_exec_function_stats dynamic management view
ms.assetid: 4c3d6a02-08e4-414b-90be-36b89a0e5a3a
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e67a50287e0878a3dcc0779bb4a78dbcbbdd0260
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68259254"
---
# <a name="sysdmexecfunctionstats-transact-sql"></a>sys.dm_exec_function_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Возвращает суммарную статистику производительности для кэшированных функций. Представление возвращает по одной строке для каждого плана кэшированной функции, а время существования строки до тех пор, пока она остается в кэше. Когда функция удаляется из кэша, соответствующая строка исключается из этого представления. В этот момент возникает аналогичную события трассировки SQL статистики производительности **sys.dm_exec_query_stats**. Возвращает сведения о скалярных функциях, включая функции в памяти и скалярные функции CLR. Не возвращает сведения о возвращающих табличное значение функций.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Чтобы избежать раскрытия этих сведений, все строки, содержащие данные, не принадлежащие к подключенному клиенту, фильтруются.  
  
> [!NOTE]
> Начальный запрос представления **sys.dm_exec_function_stats** может выдавать неточные результаты, если рабочая нагрузка в данный момент на сервере. Более точные результаты могут быть получены при повторном выполнении запроса.  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, в которой находится функция.|  
|**object_id**|**int**|Идентификационный номер объекта функции.|  
|**type**|**char(2)**|Тип объекта:   FN = скалярных функций|  
|**type_desc**|**nvarchar(60)**|Описание типа объекта: SQL_SCALAR_FUNCTION|  
|**sql_handle**|**varbinary(64)**|Это может использоваться для корреляции с запросами в **sys.dm_exec_query_stats** , которые выполнялись из этой функции.|  
|**plan_handle**|**varbinary(64)**|Идентификатор плана в оперативной памяти. Этот идентификатор является временным и константным, только пока план сохраняется в кэше. Это значение может быть использовано с **sys.dm_exec_cached_plans** динамическое административное представление.<br /><br /> Всегда будет равно 0x000, если скомпилированная функция запросы, оптимизированной для памяти таблицы.|  
|**cached_time**|**datetime**|Время, по которому функция был добавлен в кэш.|  
|**last_execution_time**|**datetime**|Последнее время, по которому выполнялась функция.|  
|**execution_count**|**bigint**|Количество раз, так как оно будет выполнена функция последней компиляции.|  
|**total_worker_time**|**bigint**|Общее время ЦП в микросекундах, затраченное на выполнение этой функции, с момента его компиляции.<br /><br /> Для скомпилированных функций **total_worker_time** могут быть неточными, если меньше миллисекунды.|  
|**last_worker_time**|**bigint**|Время ЦП, в микросекундах, затраченное время последнего выполнения функции. <sup>1</sup>|  
|**min_worker_time**|**bigint**|Минимальное время ЦП в микросекундах, которое эта функция тратил за одно выполнение. <sup>1</sup>|  
|**max_worker_time**|**bigint**|Максимальное время ЦП в микросекундах, которое эта функция тратил за одно выполнение. <sup>1</sup>|  
|**total_physical_reads**|**bigint**|Общее количество операций физического считывания при выполнении этой функции с момента его компиляции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**last_physical_reads**|**bigint**|Количество операций физического считывания выполнена время последнего выполнения функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**min_physical_reads**|**bigint**|Минимальное количество операций физического считывания за одно выполнение операций этой функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**max_physical_reads**|**bigint**|Максимальное количество операций физического считывания за одно выполнение операций этой функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**total_logical_writes**|**bigint**|Общее число логических операций записи при выполнении этой функции с момента его компиляции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**last_logical_writes**|**bigint**|Количество страниц в буферном пуле, загрязненных во время последнего выполнения плана. Если страница уже является «грязной» (т. е. измененной), операции записи не учитываются.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**min_logical_writes**|**bigint**|Минимальное количество операций логической записи за одно выполнение операций этой функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**max_logical_writes**|**bigint**|Максимальное количество операций логической записи за одно выполнение операций этой функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**total_logical_reads**|**bigint**|Общее количество операций логического считывания при выполнении этой функции с момента его компиляции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**last_logical_reads**|**bigint**|Количество операций логического считывания выполнена время последнего выполнения функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**min_logical_reads**|**bigint**|Минимальное количество операций логического считывания за одно выполнение операций этой функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**max_logical_reads**|**bigint**|Максимальное количество операций логического считывания за одно выполнение операций этой функции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**total_elapsed_time**|**bigint**|Общее затраченное время в микросекундах, выполнение этой функции.|  
|**last_elapsed_time**|**bigint**|Затраченное время в микросекундах, последнее выполнение этой функции.|  
|**min_elapsed_time**|**bigint**|Минимальное время, в микросекундах завершил выполнение этой функции.|  
|**max_elapsed_time**|**bigint**|Максимальное время, в микросекундах завершил выполнение этой функции.|  
|**total_page_server_reads**|**bigint**|Общее число страниц сервера операций считывания при выполнении этой функции с момента его компиляции.<br /><br /> **Область применения:** Гипермасштабируемый базы данных Azure SQL.|  
|**last_page_server_reads**|**bigint**|Число операций чтения страниц сервера выполнена время последнего выполнения функции.<br /><br /> **Область применения:** Гипермасштабируемый базы данных Azure SQL.|  
|**min_page_server_reads**|**bigint**|Минимальное число server страница считывает, что эта функция когда-либо выполнил за одно выполнение.<br /><br /> **Область применения:** Гипермасштабируемый базы данных Azure SQL.|  
|**max_page_server_reads**|**bigint**|Максимальное число страниц сервера считывает, что эта функция когда-либо выполнил за одно выполнение.<br /><br /> **Область применения:** Гипермасштабируемый базы данных Azure SQL.|
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратора сервера** или **администратор Azure Active Directory** учетной записи.   
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает сведения о верхней десять функций, определенных по среднему затраченному времени.  
  
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
  
  
