---
title: sys. dm_os_job_object (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 04/17/2018
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_resource_stats
- sys.dm_db_resource_stats_TSQL
- dm_db_resource_stats
- dm_db_resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_resource_stats
- dm_db_resource_stats
ms.assetid: 6e76b39f-236e-4bbf-b0b5-38be190d81e8
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 43063bb56607d1b5a21ae04b40ee4c7a17825521
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67900138"
---
# <a name="sysdm_os_job_object-azure-sql-database"></a>sys.dm_os_job_object (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Возвращает одну строку, описывающую конфигурацию объекта задания, управляющего SQL Server процессом, а также определенную статистику потребления ресурсов на уровне объектов задания. Возвращает пустой набор, если SQL Server не выполняется в объекте задания. 

Объект задания — это конструкция Windows, которая реализует управление ресурсами ЦП, памяти и ввода-вывода на уровне операционной системы. Дополнительные сведения об объектах заданий см. в разделе [объекты задания](/windows/desktop/ProcThread/job-objects). 
  
|Столбцы|Тип данных|Description|  
|-------------|---------------|-----------------|  
|cpu_rate|**int**|Указывает часть циклов процессора, которые SQL Server потоки могут использовать во время каждого интервала планирования. Значение указывается как процент доступных циклов в течение интервала планирования в 10000 циклов. Например, значение 100 означает, что потоки могут использовать ядра ЦП — их полная емкость.|
|cpu_affinity_mask|**bigint**|Битовая маска, описывающая логические процессоры, которые процесс SQL Server может использовать в группе процессоров. Например, cpu_affinity_mask 255 (1111 1111 в двоичном формате) означает, что можно использовать первые восемь логических процессоров.|
|cpu_affinity_group|**int**|Номер группы процессоров, используемой SQL Server.|
|memory_limit_mb|**bigint**|Максимальный объем зафиксированной памяти (в МБ), в течение которого все процессы в объекте задания, включая SQL Server, могут использоваться кумулятивно.| 
|process_memory_limit_mb |**bigint**|Максимальный объем зафиксированной памяти (в МБ), который может использовать один процесс в объекте задания, например SQL Server.|
|workingset_limit_mb |**bigint**|Максимальный объем памяти (в МБ), который может использовать SQL Server рабочий набор.|
|non_sos_mem_gap_mb|**bigint**|Объем памяти (в МБ), заданный для стеков потоков, библиотек DLL и других операций выделения памяти, не относящихся к SOS. Целевая память SOS — это разница `process_memory_limit_mb` между `non_sos_mem_gap_mb`и.| 
|low_mem_signal_threshold_mb|**bigint**|Пороговое значение памяти в МБ. Когда объем доступной памяти для объекта задания ниже этого порога, в процесс SQL Server отправляется сигнал о нехватке памяти. |
|total_user_time|**bigint**|Общее число 100 единиц записи NS, которые потоки в объекте задания тратили в пользовательском режиме, так как был создан объект задания. |
|total_kernel_time |**bigint**|Общее число 100 единиц записи NS, которые потоки в объекте задания тратили в режиме ядра, так как был создан объект задания. |
|write_operation_count |**bigint**|Общее число операций записи ввода-вывода на локальных дисках, выданных SQL Server с момента создания объекта задания. |
|read_operation_count |**bigint**|Общее число операций чтения ввода-вывода на локальных дисках, выданных SQL Server с момента создания объекта задания. |
|peak_process_memory_used_mb|**bigint**|Пиковый объем памяти (в МБ), в течение которого один процесс в объекте задания, например SQL Server, использовался с момента создания объекта задания.| 
|peak_job_memory_used_mb|**bigint**|Пиковый объем памяти (в МБ), в течение которого все процессы в объекте задания использовались кумулятивно с момента создания объекта задания.|
  
## <a name="permissions"></a>Разрешения  
Для Управляемый экземпляр Базы данных SQL требуется `VIEW SERVER STATE` разрешение. В Базе данных SQL требуется соответствующее разрешение `VIEW DATABASE STATE`.  
 
## <a name="see-also"></a>См. также:  

Дополнительные сведения об управляемых экземплярах см. в разделе [управляемый экземпляр базы данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
  
