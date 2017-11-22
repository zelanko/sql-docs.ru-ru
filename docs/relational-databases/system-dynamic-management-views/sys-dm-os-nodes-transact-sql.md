---
title: "sys.dm_os_nodes (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/19/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_nodes
- dm_os_nodes_TSQL
- dm_os_nodes
- sys.dm_os_nodes_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_nodes dynamic management view
ms.assetid: c768b67c-82a4-47f5-850b-0ea282358d50
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5cf36f7156f9297231fc232e8fecafee5e77427c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosnodes-transact-sql"></a>sys.dm_os_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Внутренний компонент с именем SQLOS создает структуры узлов, имитирующие аппаратное размещение ЦП. Указанные структуры могут быть изменены с помощью программной архитектуры NUMA, используемой для создания пользовательских макетов узлов.  
  
 Сведения об указанных узлах приведены в следующей таблице.  
  
> **Примечание:** для вызова этого динамического административного Представления из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_nodes**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|node_id|**smallint**|Идентификатор узла.|  
|node_state_desc|**nvarchar(256)**|Описание состояния узла. Сначала отображаются взаимоисключающие значения, затем все их комбинации. Например:<br /><br /> «В сети», «Недостаток ресурсов потоков», «Отложенный с вытеснением»<br /><br /> Существует четыре взаимоисключающих значения параметра node_state_desc. Они перечислены ниже с описаниями.<br /><br /> СЕТИ: Узел находится в сети<br /><br /> В автономном режиме: Узел находится в автономном режиме<br /><br /> Время ПРОСТОЯ: Узел имеет нет ожидающих обработки запросов и он перешел в состояние простоя.<br /><br /> IDLE_READY: Узел не имеет ожидающих обработки запросов и готова к переходу в состояние бездействия.<br /><br /> Существует пять комбинации значения параметра node_state_desc, перечисленных ниже с описаниями.<br /><br /> Приложения уровня данных: Данный узел зарезервирован для выделенного административного соединения.<br /><br /> THREAD_RESOURCES_LOW: Нет новых потоков можно создать на данном узле из-за нехватки памяти.<br /><br /> ГОРЯЧИЙ ДОБАВЛЕН: Указывает, что узлы были добавлены в ответ на горячей добавить событие ЦП.|  
|memory_object_address|**varbinary(8)**|Адрес объекта памяти, связанного с данным узлом. Связь «один к одному» для представления sys.dm_os_memory_objects.memory_object_address.|  
|memory_clerk_address|**varbinary(8)**|Адрес клерка памяти, связанного с данным узлом. Отношение «один к одному» для представления sys.dm_os_memory_clerks.memory_clerk_address.|  
|io_completion_worker_address|**varbinary(8)**|Адрес исполнителя, связанного с завершением сеанса ввода-вывода для данного узла. Отношение «один к одному» для представления sys.dm_os_workers.worker_address.|  
|memory_node_id|**smallint**|Идентификатор узла памяти, к которому принадлежит данный узел. Отношение «многие к одному» для представления sys.dm_os_memory_nodes.memory_node_id.|  
|cpu_affinity_mask|**bigint**|Битовая карта, идентифицирующая процессоры, с которыми связан данный узел.|  
|online_scheduler_count|**smallint**|Количество планировщиков в сети, управляемых данным узлом.|  
|idle_scheduler_count|**smallint**|Количество планировщиков в сети, не имеющих активных исполнителей.|  
|active_worker_count|**int**|Количество исполнителей, активных на всех планировщиках, управляемых данным узлом.|  
|avg_load_balance|**int**|Среднее количество задач, выполняемых одним планировщиком на данном узле.|  
|timer_task_affinity_mask|**bigint**|Битовая карта, определяющая планировщиков, которым можно назначить временные задачи.|  
|permanent_task_affinity_mask|**bigint**|Битовая карта, определяющая планировщиков, которым можно назначить постоянные задачи.|  
|resource_monitor_state|**bit**|Каждому узлу соответствует отдельный монитор ресурсов. Монитор ресурсов может находиться в состоянии работы или бездействия. Значению 1 соответствует рабочее состояние, значение 0 означает бездействие.|  
|online_scheduler_mask|**bigint**|Идентифицирует маску схожести процессов для этого узла.|  
|processor_group|**smallint**|Идентифицирует группу процессоров для этого узла.|  
|cpu_count |**int** |Количество процессоров, доступных для данного узла. |
|pdw_node_id|**int**|Идентификатор для узла, это распределение.<br /><br /> **Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>Permissions  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.  
  
## <a name="see-also"></a>См. также:  
  
 [Относящиеся к операционной системе SQL Server динамические административные представления &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [Архитектура Soft-NUMA (SQL Server)](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  


