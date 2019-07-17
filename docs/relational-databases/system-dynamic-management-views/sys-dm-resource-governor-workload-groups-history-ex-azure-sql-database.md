---
title: sys.dm_resource_governor_workload_groups_history_ex (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_workload_groups_history_ex_TSQL
- sys.dm_resource_governor_workload_groups_history_ex
- dm_resource_governor_workload_groups_history_ex
- dm_resource_governor_workload_groups_history_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_resource_governor_workload_groups_history_ex dynamic management view
author: joesackmsft
ms.author: josack
ms.openlocfilehash: ac776813cb817d1357948091bfc48c981fa8e730
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053259"
---
# <a name="sysdmresourcegovernorworkloadgroupshistoryex-azure-sql-database"></a>sys.dm_resource_governor_workload_groups_history_ex (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Возвращает моментальный снимок с интервалом 15 секунд для ресурсов за последние 30 минут пулов статистики для базы данных SQL Azure.
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**pool_id**| ssNoversion |Идентификатор пула ресурсов. Не допускает значение NULL.|
|**group_id**| ssNoversion |Идентификатор группы рабочей нагрузки. Не допускает значение NULL.|
|**name**| nvarchar(256) |Имя группы рабочей нагрузки. Не допускает значение NULL.|
|**snapshot_time**| datetime |Дата и время моментального снимка stats группы ресурсов, сделанного.|
|**duration_ms**| ssNoversion |Длительность между текущим и предыдущим снимками.|
|**active_worker_count**| ssNoversion |Общее количество рабочих процессов в текущий моментальный снимок.|
|**active_request_count**| ssNoversion |Текущее количество запросов. Не допускает значение NULL.|
|**active_session_count**| ssNoversion |Всего активных сеансов в текущий моментальный снимок.|
|**total_request_count**| BIGINT |Совокупное количество выполненных запросов в группе рабочей нагрузки. Не допускает значение NULL.|
|**delta_request_count**| ssNoversion |Количество выполненных запросов в группе рабочей нагрузки с момента последнего моментального снимка. Не допускает значение NULL.|
|**total_cpu_usage_ms**| BIGINT |Совокупное использование ЦП, в миллисекундах, для группы рабочей нагрузки. Не допускает значение NULL.|
|**delta_cpu_usage_ms**| ssNoversion |Использование ЦП в миллисекундах с момента создания последнего моментального снимка. Не допускает значение NULL.|
|**delta_cpu_usage_preemptive_ms**| ssNoversion |Вызовы с вытеснением win32 не регулируются по SQL-RG ЦП, с момента последнего моментального снимка.|
|**delta_reads_reduced_memgrant_count**| ssNoversion |Число операций выделения памяти достиг максимально допустимого размера запроса с момента последнего моментального снимка. Не допускает значение NULL.|
|**reads_throttled**| ssNoversion |Общее количество операций считывания регулирование.|
|**delta_reads_queued**| ssNoversion |Общего чтения, поставленных с момента последнего моментального снимка. Допускает значение NULL. Значение NULL, если группа ресурсов не управляется в аспекте операций ввода-ВЫВОДА.|
|**delta_reads_issued**| ssNoversion |Общее чтение IOs со времени последнего моментального снимка. Допускает значение NULL. Значение NULL, если группа ресурсов не управляется в аспекте операций ввода-ВЫВОДА.|
|**delta_reads_completed**| ssNoversion |Общее чтение IOs, выполненных с момента последнего моментального снимка. Не допускает значение NULL.|
|**delta_read_bytes**| BIGINT |Общее число байтов, считанных с последнего моментального снимка. Не допускает значение NULL.|
|**delta_read_stall_ms**| ssNoversion |Общее время (в миллисекундах) между получением ввода-ВЫВОДА и завершением с момента последнего моментального снимка. Не допускает значение NULL.|
|**delta_read_stall_queued_ms**| ssNoversion |Общее время (в миллисекундах) между чтения получением ввода-ВЫВОДА и проблему с момента последнего моментального снимка. Допускает значение NULL. Значение NULL, если группа ресурсов не управляется в аспекте операций ввода-ВЫВОДА. Delta_read_stall_queued_ms ненулевое значение означает, что операции ввода-ВЫВОДА зависит от RG.|
|**delta_writes_queued**| ssNoversion |Общая сумма записи вывода в очереди с момента последнего моментального снимка. Допускает значение NULL. Значение NULL, если группа ресурсов не управляется в аспекте операций ввода-ВЫВОДА.|
|**delta_writes_issued**| ssNoversion |Общая сумма записи IOs со времени последнего моментального снимка. Допускает значение NULL. Значение NULL, если группа ресурсов не управляется в аспекте операций ввода-ВЫВОДА.|
|**delta_writes_completed**| ssNoversion |Общая сумма вывода, выполненных с момента последнего моментального снимка записи. Не допускает значение NULL.|
|**delta_writes_bytes**| BIGINT |Общее число байтов, записанных с момента последнего моментального снимка. Не допускает значение NULL.|
|**delta_write_stall_ms**| ssNoversion |Общее время (в миллисекундах) между получением ввода-ВЫВОДА при записи и завершением с момента последнего моментального снимка. Не допускает значение NULL.|
|**delta_background_writes**| ssNoversion |Всего операций записи, выполненных фоновых задач с момента последнего моментального снимка.|
|**delta_background_write_bytes**| BIGINT |Размер всего записи, выполненных фоновых задач с момента последнего моментального снимка, в байтах.|
|**delta_log_bytes_used**| BIGINT |Журнал, используемый с момента последнего моментального снимка, в байтах.|
|**delta_log_temp_db_bytes_used**| BIGINT |Журнал базы данных tempdb, используемый с момента последнего моментального снимка, в байтах.|
|**delta_query_optimizations**| BIGINT |Количество операций по оптимизации запросов в данной группе рабочей нагрузки с момента последнего моментального снимка. Не допускает значение NULL.|
|**delta_suboptimal_plan_generations**| BIGINT |Число поколений неоптимальный план, произошедших в данной группе рабочей нагрузки из-за нехватки памяти с момента последнего моментального снимка. Не допускает значение NULL.
|**max_memory_grant_kb**| BIGINT |Максимальный объем памяти предоставить для группы в КБ.|
|**max_request_cpu_msec**| BIGINT |Максимальное использование ЦП, в миллисекундах, для отдельного запроса. Не допускает значение NULL.|
|**max_concurrent_request**| ssNoversion |Текущее значение параметра максимального числа параллельных запросов. Не допускает значение NULL.|
|**max_io**| ssNoversion |Максимальное ограничение ввода-ВЫВОДА для группы.|
|**max_global_io**| ssNoversion |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.
|**max_queued_io**| ssNoversion |Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.|
|**max_log_rate_kb**| BIGINT |Скорость максимального (килограмм байт / с) на уровне группы ресурсов.|
|**max_session**| ssNoversion |Ограничение сеансов для группы.|
|**max_worker**| ssNoversion |Количества работников группы.|
|||

## <a name="permissions"></a>Разрешения

В этом представлении требуется разрешение VIEW SERVER STATE.

## <a name="remarks"></a>Примечания

Пользователи могут обращаться к это динамическое административное представление для мониторинга практически в реальном времени о потреблении ресурсов пула рабочей нагрузки пользователей, а также внутренний пулы системных экземпляра базы данных SQL Azure.

> [!IMPORTANT]
> Большая часть данных, созданным это динамическое административное Представление предназначен для внутреннего использования и подлежит изменению.

## <a name="examples"></a>Примеры

В следующем примере возвращается максимальный объем данных журнала ставка и показатель потребления на каждый моментальный снимок пулом пользователя:

```sql
SELECT snapshot_time,
       name,
       max_log_rate_kb,
       delta_log_bytes_used
FROM sys.dm_resource_governor_workload_groups_history_ex
WHERE name LIKE 'User%'
ORDER BY snapshot_time DESC;
```

## <a name="see-also"></a>См. также

- [Перевод журнала скорость руководства](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [Ограничениями ресурсов эластичного пула DTU](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools)
- [Ограничения ресурсов виртуальных ядер эластичного пула](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools)
