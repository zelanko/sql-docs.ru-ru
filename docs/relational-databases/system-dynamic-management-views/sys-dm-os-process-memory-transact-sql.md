---
title: "sys.dm_os_process_memory (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_process_memory_TSQL
- dm_os_process_memory_TSQL
- dm_os_process_memory
- sys.dm_os_process_memory
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_process_memory dynamic management view
ms.assetid: e838130c-95d4-4605-9e3b-eb0ab71cd250
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3031089c848bf8afeac9eeb464dee551aecd771e
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmosprocessmemory-transact-sql"></a>sys.dm_os_process_memory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  В большинстве случаев можно управлять памятью, выделяемой процессу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с помощью диалоговых окон, позволяющих отслеживать распределение памяти и вести ее учет. Однако распределение памяти может осуществляться в адресном пространстве [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] путем вызова внутренних процедур управления памятью. Значения получаются через вызовы к базовой операционной системе. Они не используют внутренние методы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], кроме тех случаев, когда производится распределение фиксированных или больших страниц памяти.  
  
 Все возвращаемые значения объемов памяти отображаются в килобайтах (КБ). Столбец **total_virtual_address_space_reserved_kb** является дубликатом **virtual_memory_in_bytes** из **sys.dm_os_sys_info**.  
  
 Следующая таблица содержит полную информацию об адресном пространстве процессов.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_process_memory**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**physical_memory_in_use_kb**|**bigint**|Указывает суммарный объем рабочего множества процессов в КБ (по данным операционной системы) и отслеживаемой памяти, выделенной с помощью больших страниц и API-интерфейсов расширений AWE. Не допускает значения NULL.|  
|**large_page_allocations_kb**|**bigint**|Указывает физическую память, выделенную с помощью API-интерфейсов больших страниц. Не допускает значения NULL.|  
|**locked_page_allocations_kb**|**bigint**|Указывает страницы памяти, заблокированные в памяти. Не допускает значения NULL.|  
|**total_virtual_address_space_kb**|**bigint**|Указывает общий объем виртуального адресного пространства в пользовательском режиме. Не допускает значения NULL.|  
|**virtual_address_space_reserved_kb**|**bigint**|Указывает общий объем виртуального адресного пространства, зарезервированного процессом. Не допускает значения NULL.|  
|**virtual_address_space_committed_kb**|**bigint**|Указывает объем зарезервированного виртуального адресного пространства, зафиксированного или сопоставленного с физическими страницами. Не допускает значения NULL.|  
|**virtual_address_space_available_kb**|**bigint**|Указывает объем виртуального адресного пространства, свободного в данный момент. Не допускает значения NULL.<br /><br /> **Примечание:** свободной области, которые меньше, чем гранулярность выделения может существовать. Эти области недоступны для выделений.|  
|**page_fault_count**|**bigint**|Указывает количество ошибок страниц, вызванных процессом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значения NULL.|  
|**memory_utilization_percentage**|**int**|Указывает долю зафиксированной памяти в рабочем множестве, в процентах. Не допускает значения NULL.|  
|**available_commit_limit_kb**|**bigint**|Указывает объем памяти, доступной для размещения процесса. Не допускает значения NULL.|  
|**process_physical_memory_low**|**бит**|Указывает, что процесс обрабатывает уведомление о нехватке физической памяти. Не допускает значения NULL.|  
|**process_virtual_memory_low**|**бит**|Указывает, что обнаружена нехватка виртуальной памяти. Не допускает значения NULL.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения  
 На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо разрешение VIEW SERVER STATE на сервере.  
  
 На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Premium необходимо разрешение VIEW DATABASE STATE в базе данных. На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Standard и Basic требуется [!INCLUDE[ssSDS](../../includes/sssds-md.md)] учетная запись администратора.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Относящиеся к операционной системе SQL Server динамические административные представления &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


