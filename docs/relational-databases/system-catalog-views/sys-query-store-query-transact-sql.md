---
title: sys. query_store_query (Transact-SQL) | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68067966"
---
# <a name="sysquery_store_query-transact-sql"></a>sys. query_store_query (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Содержит сведения о запросе и связанную с ним общую статистику выполнения среды выполнения.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**query_id**|**bigint**|Первичный ключ.|  
|**query_text_id**|**bigint**|Внешний ключ. Присоединение к [sys. query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)|  
|**context_settings_id**|**bigint**|Внешний ключ. Присоединяет к [sys. query_context_settings &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md).<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|  
|**object_id**|**bigint**|Идентификатор объекта базы данных, частью которого является запрос (хранимая процедура, триггер, CLR UDF/функции и т. д.). 0, если запрос не выполняется как часть объекта базы данных (Специальный запрос).<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|  
|**batch_sql_handle**|**varbinary (64)**|Идентификатор пакета инструкций, частью которого является запрос. Заполняется, только если запрос ссылается на временные таблицы или табличные переменные.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать *значение NULL*.|  
|**query_hash**|**Binary (8)**|Хэш MD5 отдельного запроса, основанный на дереве логических запросов. Включает подсказки оптимизатора.|  
|**is_internal_query**|**bit**|Запрос был создан внутренним образом.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|  
|**query_parameterization_type**|**tinyint**|Тип параметризации:<br /><br /> 0 — нет<br /><br /> 1 — пользователь<br /><br /> 2 — простой<br /><br /> 3 — принудительно<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|  
|**query_parameterization_type_desc**|**nvarchar (60)**|Текстовое описание для типа параметризации.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать *значение None*.|  
|**initial_compile_start_time**|**datetimeoffset**|Время начала компиляции.|  
|**last_compile_start_time**|**datetimeoffset**|Время начала компиляции.|  
|**last_execution_time**|**datetimeoffset**|Время последнего выполнения ссылается на последнее время окончания запроса или плана.|  
|**last_compile_batch_sql_handle**|**varbinary (64)**|Обработка последнего пакета SQL, в котором последний раз использовался запрос. Его можно указать в качестве входных данных для [sys. dm_exec_sql_text &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md) , чтобы получить полный текст пакета.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать *значение NULL*.|  
|**last_compile_batch_offset_start**|**bigint**|Сведения, которые можно указать в sys. dm_exec_sql_text вместе с last_compile_batch_sql_handle.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|
|**last_compile_batch_offset_end**|**bigint**|Сведения, которые можно указать в sys. dm_exec_sql_text вместе с last_compile_batch_sql_handle.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|  
|**count_compiles**|**bigint**|Статистика компиляции.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать один (1).|  
|**avg_compile_duration**|**float**|Статистика компиляции в микросекундах.|  
|**last_compile_duration**|**bigint**|Статистика компиляции в микросекундах.|  
|**avg_bind_duration**|**float**|Статистика привязки в микросекундах.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|  
|**last_bind_duration**|**bigint**|Статистика привязки.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|  
|**avg_bind_cpu_time**|**float**|Статистика привязки.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|  
|**last_bind_cpu_time**|**bigint**|Статистика привязки.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|  
|**avg_optimize_duration**|**float**|Статистика оптимизации в микросекундах.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|
|**last_optimize_duration**|**bigint**|Статистика оптимизации.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|
|**avg_optimize_cpu_time**|**float**|Статистика оптимизации в микросекундах.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|
|**last_optimize_cpu_time**|**bigint**|Статистика оптимизации.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|
|**avg_compile_memory_kb**|**float**|Статистика памяти компиляции.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|
|**last_compile_memory_kb**|**bigint**|Статистика памяти компиляции.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|
|**max_compile_memory_kb**|**bigint**|Статистика памяти компиляции.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|
|**is_clouddb_internal_query**|**bit**|Всегда равно 0 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в локальной среде.<br/>**Примечание.** Хранилище данных SQL Azure всегда будет возвращать ноль (0).|
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **View Database State** .  
  
## <a name="see-also"></a>См. также:  
 [sys. database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys. query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys. query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys. query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys. query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys. query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys. query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Хранимые процедуры хранилища запросов &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [sys. fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  
