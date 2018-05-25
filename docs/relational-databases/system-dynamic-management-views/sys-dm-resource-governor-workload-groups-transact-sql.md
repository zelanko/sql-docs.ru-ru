---
title: sys.dm_resource_governor_workload_groups (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_workload_groups
- sys.dm_resource_governor_workload_groups_TSQL
- dm_resource_governor_workload_groups
- dm_resource_governor_workload_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_workload_groups dynamic management view
ms.assetid: f63c4914-1272-43ef-b135-fe1aabd953e0
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 023dc1559ade2a14be43750acd783fefd000e7b0
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmresourcegovernorworkloadgroups-transact-sql"></a>sys.dm_resource_governor_workload_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Возвращает статистику группы рабочей нагрузки и текущую конфигурацию группы рабочей нагрузки в памяти. Это представление можно объединить с представлением sys.dm_resource_governor_resource_pools для получения имени пула ресурсов.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_resource_governor_workload_groups**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|group_id|**int**|Идентификатор группы рабочей нагрузки. Не допускает значение NULL.|  
|имя|**sysname**|Имя группы рабочей нагрузки. Не допускает значение NULL.|  
|pool_id|**int**|Идентификатор пула ресурсов. Не допускает значение NULL.|  
|external_pool_id|**int**|**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Идентификатор для внешнего пула ресурсов. Не допускает значение NULL.|  
|statistics_start_time|**datetime**|Время, когда был выполнен сброс коллекции статистики для группы рабочей нагрузки. Не допускает значение NULL.|  
|total_request_count|**bigint**|Совокупное количество выполненных запросов в группе рабочей нагрузки. Не допускает значение NULL.|  
|total_queued_request_count|**bigint**|Совокупное количество запросов, помещенных в очередь по достижении предельного значения GROUP_MAX_REQUESTS. Не допускает значение NULL.|  
|active_request_count|**int**|Текущее количество запросов. Не допускает значение NULL.|  
|queued_request_count|**int**|Текущее количество запросов, помещенных в очередь. Не допускает значение NULL.|  
|total_cpu_limit_violation_count|**bigint**|Совокупное количество запросов, превышающих предельное значение, заданное для ЦП. Не допускает значение NULL.|  
|total_cpu_usage_ms|**bigint**|Совокупное использование ЦП, в миллисекундах, для группы рабочей нагрузки. Не допускает значение NULL.|  
|max_request_cpu_time_ms|**bigint**|Максимальное использование ЦП, в миллисекундах, для отдельного запроса. Не допускает значение NULL.<br /><br /> **Примечание:** это измеряемое значение, в отличие от request_max_cpu_time_sec, которое является значением настраиваемого параметра. Дополнительные сведения см. в разделе [Класс событий CPU Threshold Exceeded](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).|  
|blocked_task_count|**int**|Текущее количество заблокированных задач. Не допускает значение NULL.|  
|total_lock_wait_count|**bigint**|Совокупное количество возникших ожиданий блокировок. Не допускает значение NULL.|  
|total_lock_wait_time_ms|**bigint**|Совокупная продолжительность блокировки в миллисекундах. Не допускает значение NULL.|  
|total_query_optimization_count|**bigint**|Совокупное количество операций по оптимизации запросов в данной группе рабочей нагрузки. Не допускает значение NULL.|  
|total_suboptimal_plan_generation_count|**bigint**|Совокупное количество неоптимальных планов, созданных в данной группе рабочей нагрузки по причине нехватки памяти. Не допускает значение NULL.|  
|total_reduced_memgrant_count|**bigint**|Совокупное количество операций предоставления памяти, достигших максимально допустимого размера запроса. Не допускает значение NULL.|  
|max_request_grant_memory_kb|**bigint**|Максимальный объем предоставленной памяти, в килобайтах, для отдельного запроса после сброса статистики. Не допускает значение NULL.|  
|active_parallel_thread_count|**bigint**|Текущее количество используемых параллельных потоков. Не допускает значение NULL.|  
|importance|**sysname**|Текущее значение конфигурации для относительной важности запроса в данной группе рабочей нагрузки. Важность принимает одно из следующих, со средним используется по умолчанию: низкий, средний и высокий.<br /><br /> Не допускает значение NULL.|  
|request_max_memory_grant_percent|**int**|Текущее значение параметра максимального объема предоставляемой памяти, в процентах, для отдельного запроса. Не допускает значение NULL.|  
|request_max_cpu_time_sec|**int**|Текущее значение параметра максимально допустимого использования ЦП, в секундах, для отдельного запроса. Не допускает значение NULL.|  
|request_memory_grant_timeout_sec|**int**|Текущее значение параметра времени ожидания предоставления, в секундах, для отдельного запроса. Не допускает значение NULL.|  
|group_max_requests|**int**|Текущее значение параметра максимального числа параллельных запросов. Не допускает значение NULL.|  
|max_dop|**int**|Максимальная степень параллелизма для группы рабочей нагрузки. Для значения по умолчанию 0 используются глобальные параметры. Не допускает значение NULL.|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="remarks"></a>Примечания  
 Данное динамическое административное представление отображает конфигурацию, хранимую в памяти. Чтобы просмотреть сохраненные метаданные конфигурации, используйте представление каталога sys.resource_governor_workload_groups.  
  
 При выполнении инструкции ALTER RESOURCE GOVERNOR RESET STATISTICS успешно следующие счетчики сбрасываются: statistics_start_time, total_request_count, total_queued_request_count, total_cpu_limit_violation_count, total_cpu_usage_ms, max_request_ cpu_time_ms, total_lock_wait_count, total_lock_wait_time_ms, total_query_optimization_count, total_suboptimal_plan_generation_count, total_reduced_memgrant_count и max_request_grant_memory_kb. statistics_start_time задаются текущей системной даты и времени, другие счетчики сбрасываются в нуль (0).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW SERVER STATE.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)   
 [sys.resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-workload-groups-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40; Transact-SQL и &#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  



