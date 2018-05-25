---
title: sys.dm_os_job_object (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 04/17/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 8ab408179388ca10821ad79e855e39fd3ec7eb01
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmosjobobject-azure-sql-database"></a>sys.dm_os_job_object (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Возвращает одну строку, описывающую конфигурацию объект задания, который управляет процесс SQL Server, а также некоторые статистики потребления ресурсов на уровне объекта задания. Возвращает пустой набор, если SQL Server не работает в объекте задания. 

Объект задания — это конструкция Windows, который реализует регулирование ресурсов ЦП, памяти и операции ввода-ВЫВОДА на уровне операционной системы. Дополнительные сведения об объектах задания см. в разделе [объекты заданий](https://msdn.microsoft.com/library/windows/desktop/ms684161.aspx). 

> [!NOTE]
> Sys.dm_os_job_object динамическое административное Представление может в данный момент отображаются в виде sys.dm_job_object. Это временный: `sys.dm_os_job_object` будет иметь постоянное имя данного динамического административного Представления. 
  
|Столбцы|Тип данных|Описание|  
|-------------|---------------|-----------------|  
|cpu_rate|**int**|Задает часть циклов процессора, используемых потоков SQL Server во время каждого интервала планирования. Значение отображается как процент от доступных циклов в течение интервала 10000 цикл планирования. Например значение 100 означает, что потоки могут использовать ядер ЦП, их полностью.|
|cpu_affinity_mask|**bigint**|Битовая маска, описывающий какие логических процессоров процесс SQL Server можно использовать в группе процессоров. Например, cpu_affinity_mask 255 (1111 1111 в двоичном формате) означает, что первые восемь логических процессоров может использоваться.|
|cpu_affinity_group|**int**|Количество группе процессоров, используемый сервером SQL Server.|
|memory_limit_mb|**bigint**|Максимальный объем выделенной памяти (в Мегабайтах), все процессы в объект задания, включая SQL Server, можно использовать вместе.| 
|process_memory_limit_mb |**bigint**|Максимальный объем выделенной памяти (в Мегабайтах), можно использовать одного процесса в объект задания, например SQL Server.|
|workingset_limit_mb |**bigint**|Максимальный объем памяти (в Мегабайтах), можно использовать SQL Server рабочего набора.|
|non_sos_mem_gap_mb|**bigint**|Объем памяти в МБ, установленную для стеки потоков, библиотеки DLL и других операций выделения памяти не SOS. Память целевого SOS отличается от `process_memory_limit_mb` и `non_sos_mem_gap_mb`.| 
|low_mem_signal_threshold_mb|**bigint**|Порог памяти, в МБ. Когда объем доступной памяти для объекта задания меньше порогового значения, к процессу SQL Server отправляется сигнал уведомления о нехватке памяти. |
|total_user_time|**bigint**|Общее число тактов 100 нс, потоки в объект задания тратили в пользовательском режиме, с момента создания объекта задания. |
|total_kernel_time |**bigint**|Общее число тактов 100 нс, потоки в объект задания тратили в режиме ядра, с момента создания объекта задания. |
|write_operation_count |**bigint**|Общее число записи операций ввода-ВЫВОДА на локальных дисках, выданный службой SQL Server с момента создания объекта задания. |
|read_operation_count |**bigint**|Общее количество операций чтения ввода-ВЫВОДА на локальных дисках, выданный службой SQL Server с момента создания объекта задания. |
|peak_process_memory_used_mb|**bigint**|Объем памяти в МБ, что один процесс в объект задания, например SQL Server использовал с момента создания объекта задания.| 
|peak_job_memory_used_mb|**bigint**|Объем памяти (в Мегабайтах), все процессы в объект задания Суммарно использован, поскольку объект задания был создан.|
  
## <a name="permissions"></a>Разрешения  
На экземпляре управляемых базы данных SQL требуется `VIEW SERVER STATE` разрешение. В базе данных SQL, требует `VIEW DATABASE STATE` разрешений в базе данных.  
 
## <a name="see-also"></a>См. также  

Сведения об управляемых экземплярах см. в разделе [управляемый экземпляр базы данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
  
