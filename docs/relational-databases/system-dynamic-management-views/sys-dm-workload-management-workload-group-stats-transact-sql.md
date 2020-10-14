---
description: sys.dm_workload_management_workload_groups_stats (Transact-SQL)
title: sys.dm_workload_management_workload_groups_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/02/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
monikerRange: = azure-sqldw-latest||= sqlallproducts-allversions
ms.openlocfilehash: bc36846a62b8b71e0e21d7ea61d088a0f16c674d
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92035187"
---
# <a name="sysdm_workload_management_workload_groups_stats-transact-sql"></a>sys.dm_workload_management_workload_groups_stats (Transact-SQL)
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Возвращает статистику группы рабочей нагрузки и действующие значения группы рабочей нагрузки в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] .  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|group_id|**int**|Уникальный идентификатор группы рабочей нагрузки.||
|name|**sysname**|Имя группы рабочей нагрузки.||
|statistics_start_time|**datetime**|Время начала сбора статистики для группы рабочей нагрузки.  Значение задается либо при создании группы рабочей нагрузки, либо при приостановке или изменении экземпляра.||
|total_request_count|**bigint**|Совокупное количество выполненных запросов в группе рабочей нагрузки.||
|total_shared_resource_reqeusts|**bigint**|Совокупное число завершенных запросов в группе рабочей нагрузки, которые использовали ресурсы из общего пула.||
|total_queued_request_count|**bigint**|Совокупное количество запросов, поставленных в очередь после достижения предела max_concurrency.||
|total_request_execution_timeouts|**bigint**|Совокупное количество запросов в группе рабочей нагрузки, время ожидания которых истекло до завершения на основе параметра query_execution_timeout_sec.||
|effective_min_percentage_resource|**tinyint**|Действующий параметр min_percentage_resource, который допускает использование уровня обслуживания и параметров группы рабочей нагрузки. Эффективный min_percentage_resource можно изменить выше на более низких уровнях обслуживания.  Например, в DW100c наименьшее допустимое min_percentage_resource имеет значение 25%.  Если значение не может быть предоставлено на уровне службы, min_percentage_resource корректируется на 0%.  Например, если для параметра min_percentage_resource установить значение 10% в DW6000c, будет effective_min_percentage_resource 0% при уменьшении масштаба до DW100c.||
|effective_cap_percentage_resource|**tinyint**|Действующий cap_percentage_resource для группы рабочей нагрузки.  Если имеются другие группы рабочей нагрузки с min_percentage_resource > 0, effective_cap_percentage_resource меньше пропорционально.||
|effective_request_min_resource_grant_percent|**Decimal (5, 2)**|Эффективное значение времени выполнения для request_min_resource_grant_percent группы рабочей нагрузки. Эффективное значение, учитывая уровень обслуживания и настройки группы рабочей нагрузки.  Если min_percentage_resource корректируется из-за уровня обслуживания, effective_request_min_resource_grant_percent будет скорректирован соответствующим образом.||
|effective_request_max_resource_grant_percent|**Decimal (5, 2)**|Эффективное значение времени выполнения для request_max_resource_grant_percent группы рабочей нагрузки, учитывая конфигурацию всех групп рабочей нагрузки.||
|||||

## <a name="see-also"></a>См. также статью

 [Динамические административные представления Azure синапсе Analytics и Параллельное хранилище данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
