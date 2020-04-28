---
title: sys. dm_os_memory_nodes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_memory_nodes_TSQL
- sys.dm_os_memory_nodes
- sys.dm_os_memory_nodes_TSQL
- dm_os_memory_nodes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_nodes dynamic management view
ms.assetid: bf4032fe-7db1-40e9-a62e-d69cebff4b44
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6f68524b2713b9d662c9e9ed0950334ea0a94ece
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "73983134"
---
# <a name="sysdm_os_memory_nodes-transact-sql"></a>sys.dm_os_memory_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Внутреннее распределение памяти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] осуществляется с помощью диспетчера памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Отслеживание различий между счетчиками памяти процесса из **sys. dm_os_process_memory** и внутренние счетчики могут указывать на использование памяти из внешних [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компонентов в пространстве памяти.  
  
 Узлы создаются для каждого физического узла памяти NUMA. Они могут отличаться от узлов ЦП в **sys. dm_os_nodes**.  
  
 Распределение памяти, выполняемое напрямую с помощью процедур распределения памяти Windows, не отслеживается. В следующей таблице приведены данные о распределении памяти, выполненном исключительно с помощью интерфейса диспетчера памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Чтобы вызвать эту функцию [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] из [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]или, используйте имя **sys. dm_pdw_nodes_os_memory_nodes**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**memory_node_id**|**smallint**|Указывает идентификатор узла памяти. Относится к **memory_node_id** **sys. dm_os_memory_clerks**. Не допускает значения NULL.|  
|**virtual_address_space_reserved_kb**|**bigint**|Указывает объем зарезервированного виртуального адресного пространства (в КБ), которое не зафиксировано и не сопоставлено с физическими страницами. Не допускает значения NULL.|  
|**virtual_address_space_committed_kb**|**bigint**|Указывает объем виртуального адресного пространства (в КБ), зафиксированного или сопоставленного с физическими страницами. Не допускает значения NULL.|  
|**locked_page_allocations_kb**|**bigint**|Указывает объем физической памяти (в КБ), заблокированной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значения NULL.|  
|**single_pages_kb**|**bigint**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Объем зафиксированной памяти (в КБ), выделенной с помощью механизма распределения одиночных страниц узла памяти. Эта память распределяется из буферного пула. Данное значение указывает на узел, от которого исходит запрос на выделение памяти, а не на физическое положение выделенной памяти.|  
|**pages_kb**|**bigint**|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> Указывает объем зафиксированной памяти (в КБ), выделенной данным узлом NUMA с помощью механизма распределения страниц диспетчера памяти. Не допускает значения NULL.|  
|**multi_pages_kb**|**bigint**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Объем зафиксированной памяти (в КБ), выделенной с помощью механизма многостраничного распределения потоков этого узла. Указанная память выделяется из пространства, находящегося вне буферного пула. Данное значение указывает на узел, от которого исходит запрос на выделение памяти, а не на физическое положение выделенной памяти.|  
|**shared_memory_reserved_kb**|**bigint**|Указывает объем общей памяти (в КБ), зарезервированной данным узлом. Не допускает значения NULL.|  
|**shared_memory_committed_kb**|**bigint**|Указывает объем общей памяти (в КБ), зафиксированной данным узлом. Не допускает значения NULL.|  
|**cpu_affinity_mask**|**bigint**|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> Только для внутреннего применения. Не допускает значения NULL.|  
|**online_scheduler_mask**|**bigint**|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> Только для внутреннего применения. Не допускает значения NULL.|  
|**processor_group**|**smallint**|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> Только для внутреннего применения. Не допускает значения NULL.|  
|**foreign_committed_kb**|**bigint**|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> Указывает объем общей памяти (в КБ), зафиксированной другими узлами памяти. Не допускает значения NULL.|  
|**target_kb** |**bigint** |**Применимо к**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] и более [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]поздним версиям.<br /><br /> Указывает целевую память для узла памяти в КБ. |   
|**pdw_node_id**|**int**|**Применимо к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор узла, на котором находится данное распределение.|  
  
## <a name="permissions"></a>Разрешения

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   

## <a name="see-also"></a>См. также:  
  [SQL Server динамические административные представления, связанные с операционной системой &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


