---
title: sys.dm_os_job_object (база данных SQL Azure) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 074981f19f0eb74a7e7c7d4e82466957f0ff98b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63047061"
---
# <a name="sysdmosjobobject-azure-sql-database"></a>sys.dm_os_job_object (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Возвращает одну строку, описывающие конфигурацию объекта задания, управляющий процесс SQL Server, а также определенные статистику потребления ресурсов на уровне объекта задания. Возвращает пустой набор, если SQL Server не работает в объект задания. 

Объект задания — это конструкция Windows, который реализует управление ресурсами Процессора, памяти и ввода-ВЫВОДА на уровне операционной системы. Дополнительные сведения о объекты заданий, см. в разделе [объекты заданий](/windows/desktop/ProcThread/job-objects). 
  
|Столбцы|Тип данных|Описание|  
|-------------|---------------|-----------------|  
|cpu_rate|**int**|Задает часть объекта циклов процессора, потоки SQL Server можно использовать во время каждого интервала планирования. Значение указывается в процентах от доступных циклов в интервале 10000 цикл планирования. Например значение 100 означает, что потоки могут использовать ядер ЦП, их полностью.|
|cpu_affinity_mask|**bigint**|Битовая маска, описывающий, какие логические процессоры процесс SQL Server можно использовать в группе процессоров. Например, cpu_affinity_mask 255 (1111 1111 в двоичном формате) означает, что первые восемь логических процессоров может использоваться.|
|cpu_affinity_group|**int**|Число группе процессоров, используемых SQL Server.|
|memory_limit_mb|**bigint**|Максимальный объем выделенной памяти (в Мегабайтах), все процессы в объект задания, включая SQL Server, можно использовать все вместе.| 
|process_memory_limit_mb |**bigint**|Максимальный объем выделенной памяти (в Мегабайтах), одного процесса в объект задания, например SQL Server, можно использовать.|
|workingset_limit_mb |**bigint**|Максимальный объем памяти в МБ, который можно использовать в рабочем множестве сервера SQL.|
|non_sos_mem_gap_mb|**bigint**|Объем памяти в МБ, установленную для стеки потоков, библиотеки DLL и других ресурсов памяти не SOS. Память целевого SOS разница между `process_memory_limit_mb` и `non_sos_mem_gap_mb`.| 
|low_mem_signal_threshold_mb|**bigint**|Порог памяти, в МБ. Когда объем доступной памяти для объекта задания меньше порогового значения, отправляется сигнал уведомление о нехватке памяти процесса SQL Server. |
|total_user_time|**bigint**|Общее число 100 нс тактов, потоками в объекте задания на в пользовательском режиме, с момента создания объекта задания. |
|total_kernel_time |**bigint**|Общее число 100 нс тактов, потоками в объекте задания на в режиме ядра, с момента создания объекта задания. |
|write_operation_count |**bigint**|Общее число записи операций ввода-ВЫВОДА на локальных дисках, выданный службой SQL Server с момента создания объекта задания. |
|read_operation_count |**bigint**|Общее число операций чтения ввода-ВЫВОДА на локальных дисках, выданный службой SQL Server с момента создания объекта задания. |
|peak_process_memory_used_mb|**bigint**|Объем памяти в МБ, что один процесс в объект задания, например SQL Server, использовался с момента создания объекта задания.| 
|peak_job_memory_used_mb|**bigint**|Объем памяти в МБ, что все процессы в объект задания потратило использован, поскольку объект задания был создан.|
  
## <a name="permissions"></a>Разрешения  
SQL управляемом экземпляре базы данных, требуется `VIEW SERVER STATE` разрешение. В базе данных SQL, требуется `VIEW DATABASE STATE` разрешение в базе данных.  
 
## <a name="see-also"></a>См. также  

Сведения об управляемых экземплярах см. в разделе [управляемый экземпляр базы данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
  
