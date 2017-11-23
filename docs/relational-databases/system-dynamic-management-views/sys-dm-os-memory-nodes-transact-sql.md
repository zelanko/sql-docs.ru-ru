---
title: "sys.dm_os_memory_nodes (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
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
- dm_os_memory_nodes_TSQL
- sys.dm_os_memory_nodes
- sys.dm_os_memory_nodes_TSQL
- dm_os_memory_nodes
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_memory_nodes dynamic management view
ms.assetid: bf4032fe-7db1-40e9-a62e-d69cebff4b44
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5284229fd7c102ceb23e8123cd355b8be29190f0
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosmemorynodes-transact-sql"></a>sys.dm_os_memory_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Внутреннее распределение памяти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] осуществляется с помощью диспетчера памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Отслеживание разницу между счетчиков памяти из **sys.dm_os_process_memory** и внутренних счетчиков может указывать на использование памяти, из внешних компонентов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] области памяти.  
  
 Узлы создаются для каждого физического узла памяти NUMA. Они могут отличаться от узлов ЦП в **sys.dm_os_nodes**.  
  
 Распределение памяти, выполняемое напрямую с помощью процедур распределения памяти Windows, не отслеживается. В следующей таблице приведены данные о распределении памяти, выполненном исключительно с помощью интерфейса диспетчера памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_memory_nodes**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**memory_node_id**|**smallint**|Указывает идентификатор узла памяти. Они связаны с **memory_node_id** из **sys.dm_os_memory_clerks**. Не допускает значения NULL.|  
|**virtual_address_space_reserved_kb**|**bigint**|Указывает объем зарезервированного виртуального адресного пространства (в КБ), которое не зафиксировано и не сопоставлено с физическими страницами. Не допускает значения NULL.|  
|**virtual_address_space_committed_kb**|**bigint**|Указывает объем виртуального адресного пространства (в КБ), зафиксированного или сопоставленного с физическими страницами. Не допускает значения NULL.|  
|**locked_page_allocations_kb**|**bigint**|Указывает объем физической памяти (в КБ), заблокированной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значения NULL.|  
|**single_pages_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Объем зафиксированной памяти (в КБ), выделенной с помощью механизма распределения одиночных страниц узла памяти. Эта память распределяется из буферного пула. Данное значение указывает на узел, от которого исходит запрос на выделение памяти, а не на физическое положение выделенной памяти.|  
|**pages_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает объем зафиксированной памяти (в КБ), выделенной данным узлом NUMA с помощью механизма распределения страниц диспетчера памяти. Не допускает значения NULL.|  
|**multi_pages_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Объем зафиксированной памяти (в КБ), выделенной с помощью механизма многостраничного распределения потоков этого узла. Указанная память выделяется из пространства, находящегося вне буферного пула. Данное значение указывает на узел, от которого исходит запрос на выделение памяти, а не на физическое положение выделенной памяти.|  
|**shared_memory_reserved_kb**|**bigint**|Указывает объем общей памяти (в КБ), зарезервированной данным узлом. Не допускает значения NULL.|  
|**shared_memory_committed_kb**|**bigint**|Указывает объем общей памяти (в КБ), зафиксированной данным узлом. Не допускает значения NULL.|  
|**cpu_affinity_mask**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Только для внутреннего применения. Не допускает значения NULL.|  
|**online_scheduler_mask**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Только для внутреннего применения. Не допускает значения NULL.|  
|**processor_group**|**smallint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Только для внутреннего применения. Не допускает значения NULL.|  
|**foreign_committed_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает объем общей памяти (в КБ), зафиксированной другими узлами памяти. Не допускает значения NULL.|  
|**target_kb** |**bigint** |**Применяется к**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Указывает цель памяти для узла памяти, в КБ. |   
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Permissions  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.   
  
## <a name="see-also"></a>См. также:  
  [Относящиеся к операционной системе SQL Server динамические административные представления &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


