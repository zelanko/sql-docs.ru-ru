---
title: sys.query_store_query (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 082be82ea40c05f50bffb4f3904c0c6be586d473
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39547984"
---
# <a name="sysquerystorequery-transact-sql"></a>sys.query_store_query (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Содержит сведения о запросе и его связанный общий сводные статистические данные.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**query_id**|**bigint**|Первичный ключ.|  
|**query_text_id**|**bigint**|Внешний ключ. Присоединяет к [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)|  
|**context_settings_id**|**bigint**|Внешний ключ. Присоединяет к [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md).|  
|**object_id**|**bigint**|Идентификатор объекта базы данных, запрос является частью (хранимой процедуры, триггера, CLR определяемой пользователем функции или определяемой пользователем статистической функции, и т.д.). 0, если запрос не выполняется как часть объекта базы данных (запросов ad-hoc).|  
|**batch_sql_handle**|**varbinary(64)**|Идентификатор пакета, инструкции запроса является частью. Заполняется только в том случае, если запрос ссылается на временных таблиц или табличных переменных.|  
|**query_hash**|**binary(8)**|MD5-хэш отдельный запрос, основанный на дереве логического запроса. Включает в себя указания оптимизатора.|  
|**is_internal_query**|**bit**|Запрос был создаются внутри организации.|  
|**query_parameterization_type**|**tinyint**|Тип параметризации:<br /><br /> 0 — none<br /><br /> 1 — пользователь<br /><br /> 2 — простой<br /><br /> 3 — принудительно|  
|**query_parameterization_type_desc**|**nvarchar(60)**|Текстовое описание для типа параметризации.|  
|**initial_compile_start_time**|**datetimeoffset**|Время начала компиляции.|  
|**last_compile_start_time**|**datetimeoffset**|Время начала компиляции.|  
|**last_execution_time**|**datetimeoffset**|Время последнего выполнения относится к последней время окончания/плана запроса.|  
|**last_compile_batch_sql_handle**|**varbinary(64)**|Дескриптор последнего пакета SQL, в котором запрос использованный последний раз. Его можно указать в качестве входных данных для [sys.dm_exec_sql_text &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md) получить полный текст пакета.|  
|**last_compile_batch_offset_start**|**bigint**|Информация, которая может быть предоставлена в функцию sys.dm_exec_sql_text, а также last_compile_batch_sql_handle.|  
|**last_compile_batch_offset_end**|**bigint**|Информация, которая может быть предоставлена в функцию sys.dm_exec_sql_text, а также last_compile_batch_sql_handle.|  
|**count_compiles**|**bigint**|Статистика компиляции.|  
|**avg_compile_duration**|**float**|Статистика компиляции, в микросекундах.|  
|**last_compile_duration**|**bigint**|Статистика компиляции, в микросекундах.|  
|**avg_bind_duration**|**float**|Статистические данные привязки, в микросекундах.|  
|**last_bind_duration**|**bigint**|Статистические данные привязки.|  
|**avg_bind_cpu_time**|**float**|Статистические данные привязки.|  
|**last_bind_cpu_time**|**bigint**|Статистические данные привязки.|  
|**avg_optimize_duration**|**float**|Статистику оптимизации, в микросекундах.|  
|**last_optimize_duration**|**bigint**|Статистические данные оптимизации.|  
|**avg_optimize_cpu_time**|**float**|Статистику оптимизации, в микросекундах.|  
|**last_optimize_cpu_time**|**bigint**|Статистические данные оптимизации.|  
|**avg_compile_memory_kb**|**float**|Скомпилируйте Статистика использования памяти.|  
|**last_compile_memory_kb**|**bigint**|Скомпилируйте Статистика использования памяти.|  
|**max_compile_memory_kb**|**bigint**|Скомпилируйте Статистика использования памяти.|  
|**is_clouddb_internal_query**|**bit**|Всегда равно 0 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на предприятии.|  
  
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
  
  
