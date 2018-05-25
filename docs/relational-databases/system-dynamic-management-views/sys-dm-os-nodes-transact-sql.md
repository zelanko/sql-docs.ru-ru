---
title: sys.dm_os_nodes (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 02/13/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_nodes
- dm_os_nodes_TSQL
- dm_os_nodes
- sys.dm_os_nodes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_nodes dynamic management view
ms.assetid: c768b67c-82a4-47f5-850b-0ea282358d50
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f0931202ced4031ea99680a98c3cbc1d1030c629
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmosnodes-transact-sql"></a>sys.dm_os_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Внутренний компонент с именем SQLOS создает структуры узлов, имитирующие аппаратное размещение ЦП. Эти структуры могут быть изменены с помощью [программной архитектуры NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md) для создания пользовательских макетов узлов.  

> [!NOTE]
> Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] будут автоматически использовать программной архитектуры NUMA определенных конфигураций оборудования. Дополнительные сведения см. в разделе [автоматический режим программной NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md#automatic-soft-numa).
  
Сведения об указанных узлах приведены в следующей таблице.  
  
> [!NOTE]
> Для вызова этого динамического административного Представления из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_nodes**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|node_id|**smallint**|Идентификатор узла.|  
|node_state_desc|**nvarchar(256)**|Описание состояния узла. Сначала отображаются взаимоисключающие значения, затем все их комбинации. Например:<br /> «В сети», «Недостаток ресурсов потоков», «Отложенный с вытеснением»<br /><br />Существует четыре взаимоисключающих значения параметра node_state_desc. Они перечислены ниже с описаниями.<br /><ul><li>СЕТИ: Узел находится в сети<li>В автономном режиме: Узел находится в автономном режиме<li>Время ПРОСТОЯ: Узел имеет нет ожидающих обработки запросов и он перешел в состояние простоя.<li>IDLE_READY: Узел не имеет ожидающих обработки запросов и готова к переходу в состояние бездействия.</li></ul><br />Существует три комбинации значения параметра node_state_desc, перечисленных ниже с описаниями.<br /><ul><li>Приложения уровня данных: Данный узел зарезервирован для [выделенного административного соединения](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).<li>THREAD_RESOURCES_LOW: Нет новых потоков можно создать на данном узле из-за нехватки памяти.<li>ГОРЯЧИЙ ДОБАВЛЕН: Указывает, что узлы были добавлены в ответ на горячей добавить событие ЦП.</li></ul>|  
|memory_object_address|**varbinary(8)**|Адрес объекта памяти, связанного с данным узлом. Однозначное соответствие для [sys.dm_os_memory_objects](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md).memory_object_address.|  
|memory_clerk_address|**varbinary(8)**|Адрес клерка памяти, связанного с данным узлом. Однозначное соответствие для [sys.dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).memory_clerk_address.|  
|io_completion_worker_address|**varbinary(8)**|Адрес исполнителя, связанного с завершением сеанса ввода-вывода для данного узла. Однозначное соответствие для [sys.dm_os_workers](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).worker_address.|  
|memory_node_id|**smallint**|Идентификатор узла памяти, к которому принадлежит данный узел. Многие к одному отношение [sys.dm_os_memory_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-nodes-transact-sql.md).memory_node_id.|  
|cpu_affinity_mask|**bigint**|Битовая карта, идентифицирующая процессоры, с которыми связан данный узел.|  
|online_scheduler_count|**smallint**|Количество планировщиков в сети, управляемых данным узлом.|  
|idle_scheduler_count|**smallint**|Количество планировщиков в сети, не имеющих активных исполнителей.|  
|active_worker_count|**int**|Количество исполнителей, активных на всех планировщиках, управляемых данным узлом.|  
|avg_load_balance|**int**|Среднее количество задач, выполняемых одним планировщиком на данном узле.|  
|timer_task_affinity_mask|**bigint**|Битовая карта, определяющая планировщиков, которым можно назначить временные задачи.|  
|permanent_task_affinity_mask|**bigint**|Битовая карта, определяющая планировщиков, которым можно назначить постоянные задачи.|  
|resource_monitor_state|**бит**|Каждому узлу соответствует отдельный монитор ресурсов. Монитор ресурсов может находиться в состоянии работы или бездействия. Значению 1 соответствует рабочее состояние, значение 0 означает бездействие.|  
|online_scheduler_mask|**bigint**|Идентифицирует маску схожести процессов для этого узла.|  
|processor_group|**smallint**|Идентифицирует группу процессоров для этого узла.|  
|cpu_count |**int** |Количество процессоров, доступных для данного узла. |
|pdw_node_id|**int**|Идентификатор для узла, это распределение.<br /><br /> **Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="see-also"></a>См. также    
 [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [Архитектура Soft-NUMA (SQL Server)](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
