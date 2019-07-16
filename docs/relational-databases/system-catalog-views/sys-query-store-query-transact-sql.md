---
title: sys.query_store_query (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_QUERY
- SYS.QUERY_STORE_QUERY_TSQL
- SYS.QUERY_STORE_QUERY
- QUERY_STORE_QUERY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_query catalog view
- sys.query_store_query catalog view
ms.assetid: bdee149e-7556-4fc3-8242-925dd4b7b6ac
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d5b7eea64a807af96094767ef5aca00167d5946c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067966"
---
# <a name="sysquerystorequery-transact-sql"></a>sys.query_store_query (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Содержит сведения о запросе и его связанный общий сводные статистические данные.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**query_id**|**bigint**|Первичный ключ.|  
|**query_text_id**|**bigint**|Внешний ключ. Присоединяет к [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)|  
|**context_settings_id**|**bigint**|Внешний ключ. Присоединяет к [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md).<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**object_id**|**bigint**|Идентификатор объекта базы данных, запрос является частью (хранимой процедуры, триггера, CLR определяемой пользователем функции или определяемой пользователем статистической функции, и т.д.). 0, если запрос не выполняется как часть объекта базы данных (запросов ad-hoc).<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**batch_sql_handle**|**varbinary(64)**|Идентификатор пакета, инструкции запроса является частью. Заполняется только в том случае, если запрос ссылается на временных таблиц или табличных переменных.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать *NULL*.|  
|**query_hash**|**binary(8)**|MD5-хэш отдельный запрос, основанный на дереве логического запроса. Включает в себя указания оптимизатора.|  
|**is_internal_query**|**bit**|Запрос был создаются внутри организации.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**query_parameterization_type**|**tinyint**|Тип параметризации:<br /><br /> 0 — none<br /><br /> 1 – Проверка<br /><br /> 2 — простая<br /><br /> 3 - принудительно<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**query_parameterization_type_desc**|**nvarchar(60)**|Текстовое описание для типа параметризации.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать *None*.|  
|**initial_compile_start_time**|**datetimeoffset**|Время начала компиляции.|  
|**last_compile_start_time**|**datetimeoffset**|Время начала компиляции.|  
|**last_execution_time**|**datetimeoffset**|Время последнего выполнения относится к последней время окончания/плана запроса.|  
|**last_compile_batch_sql_handle**|**varbinary(64)**|Дескриптор последнего пакета SQL, в котором запрос использованный последний раз. Его можно указать в качестве входных данных для [sys.dm_exec_sql_text &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md) получить полный текст пакета.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать *NULL*.|  
|**last_compile_batch_offset_start**|**bigint**|Информация, которая может быть предоставлена в функцию sys.dm_exec_sql_text, а также last_compile_batch_sql_handle.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|
|**last_compile_batch_offset_end**|**bigint**|Информация, которая может быть предоставлена в функцию sys.dm_exec_sql_text, а также last_compile_batch_sql_handle.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**count_compiles**|**bigint**|Статистика компиляции.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать один (1).|  
|**avg_compile_duration**|**float**|Статистика компиляции, в микросекундах.|  
|**last_compile_duration**|**bigint**|Статистика компиляции, в микросекундах.|  
|**avg_bind_duration**|**float**|Статистические данные привязки, в микросекундах.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**last_bind_duration**|**bigint**|Статистические данные привязки.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**avg_bind_cpu_time**|**float**|Статистические данные привязки.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**last_bind_cpu_time**|**bigint**|Статистические данные привязки.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|  
|**avg_optimize_duration**|**float**|Статистику оптимизации, в микросекундах.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|
|**last_optimize_duration**|**bigint**|Статистические данные оптимизации.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|
|**avg_optimize_cpu_time**|**float**|Статистику оптимизации, в микросекундах.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|
|**last_optimize_cpu_time**|**bigint**|Статистические данные оптимизации.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|
|**avg_compile_memory_kb**|**float**|Скомпилируйте Статистика использования памяти.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|
|**last_compile_memory_kb**|**bigint**|Скомпилируйте Статистика использования памяти.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|
|**max_compile_memory_kb**|**bigint**|Скомпилируйте Статистика использования памяти.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|
|**is_clouddb_internal_query**|**bit**|Всегда равно 0 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на предприятии.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать нуль (0).|
  
## <a name="permissions"></a>Разрешения  
 Требуется **VIEW DATABASE STATE** разрешение.  
  
## <a name="see-also"></a>См. также  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Query Store Stored Procedures (Transact-SQL)](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  (Хранимые процедуры хранилища запросов (Transact-SQL))  
 [sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL)](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  
