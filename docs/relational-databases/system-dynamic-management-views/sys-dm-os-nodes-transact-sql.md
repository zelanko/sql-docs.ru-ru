---
title: sys.dm_os_nodes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 02/13/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2b2d0004204829225d7767c53a7d2406ff557f36
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899880"
---
# <a name="sysdmosnodes-transact-sql"></a>sys.dm_os_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Внутренний компонент с именем SQLOS создает структуры узлов, имитирующие аппаратное размещение ЦП. Эти структуры могут быть изменены с помощью [программной архитектуры NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md) для создания пользовательских макетов узлов.  

> [!NOTE]
> Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] будут автоматически использовать программной архитектуры NUMA для определенных конфигураций оборудования. Дополнительные сведения см. в разделе [автоматическая программная архитектура NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md#automatic-soft-numa).
  
Сведения об указанных узлах приведены в следующей таблице.  
  
> [!NOTE]
> Для вызова этого динамического административного Представления из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_nodes**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|node_id|**smallint**|Идентификатор узла.|  
|node_state_desc|**nvarchar(256)**|Описание состояния узла. Сначала отображаются взаимоисключающие значения, затем все их комбинации. Пример:<br /> «В сети», «Недостаток ресурсов потоков», «Отложенный с вытеснением»<br /><br />Существует четыре взаимоисключающих значения параметра node_state_desc. Они перечислены с описаниями.<br /><ul><li>ONLINE: Узел находится в сети<li>OFFLINE: Узел находится в автономном режиме<li>IDLE. Узел имеет нет ожидающих обработки запросов и он перешел в состояние простоя.<li>IDLE_READY: Узел не имеет ожидающих обработки запросов и готов к переходу в состояние бездействия.</li></ul><br />Существует три значения параметра node_state_desc, перечисленные далее вместе с описаниями.<br /><ul><li>ПРИЛОЖЕНИЯ УРОВНЯ ДАННЫХ: Данный узел зарезервирован для [выделенного административного соединения](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).<li>THREAD_RESOURCES_LOW: Новые потоки не могут создаваться на этом узле из-за условия нехватки памяти.<li>"ГОРЯЧИЙ" ДОБАВЛЕНЫ: Указывает, что узлы были добавлены в ответ с поддержкой горячей события ЦП.</li></ul>|  
|memory_object_address|**varbinary(8)**|Адрес объекта памяти, связанного с данным узлом. Отношение один к одному [sys.dm_os_memory_objects](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md).memory_object_address.|  
|memory_clerk_address|**varbinary(8)**|Адрес клерка памяти, связанного с данным узлом. Отношение один к одному [sys.dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).memory_clerk_address.|  
|io_completion_worker_address|**varbinary(8)**|Адрес исполнителя, связанного с завершением сеанса ввода-вывода для данного узла. Отношение один к одному [sys.dm_os_workers](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).worker_address.|  
|memory_node_id|**smallint**|Идентификатор узла памяти, к которому принадлежит данный узел. Связь многие к одному [sys.dm_os_memory_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-nodes-transact-sql.md).memory_node_id.|  
|cpu_affinity_mask|**bigint**|Битовая карта, идентифицирующая процессоры, с которыми связан данный узел.|  
|online_scheduler_count|**smallint**|Количество планировщиков в сети, которые управляются этим узлом.|  
|idle_scheduler_count|**smallint**|Количество планировщиков в сети, не имеющих активных исполнителей.|  
|active_worker_count|**int**|Количество исполнителей, активных на всех планировщиках, управляемых данным узлом.|  
|avg_load_balance|**int**|Среднее количество задач, выполняемых одним планировщиком на данном узле.|  
|timer_task_affinity_mask|**bigint**|Битовая карта, определяющая планировщиков, которым можно назначить временные задачи.|  
|permanent_task_affinity_mask|**bigint**|Битовая карта, определяющая планировщиков, которым можно назначить постоянные задачи.|  
|resource_monitor_state|**bit**|Каждому узлу соответствует отдельный монитор ресурсов. Монитор ресурсов может находиться в состоянии работы или бездействия. Значению 1 соответствует рабочее состояние, значение 0 означает бездействие.|  
|online_scheduler_mask|**bigint**|Идентифицирует маску схожести процессов для этого узла.|  
|processor_group|**smallint**|Идентифицирует группу процессоров для этого узла.|  
|cpu_count |**int** |Количество процессоров, доступных для данного узла. |
|pdw_node_id|**int**|Идентификатор для узла, это распределение является на.<br /><br /> **Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
В [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] необходимо разрешение `VIEW DATABASE STATE` для базы данных.   

## <a name="see-also"></a>См. также    
 [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [Архитектура Soft-NUMA (SQL Server)](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
