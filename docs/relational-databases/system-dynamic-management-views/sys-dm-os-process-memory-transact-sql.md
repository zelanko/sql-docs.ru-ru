---
title: sys. dm_os_process_memory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dc8eb11f3b77814ba9cd296cce15bba920f0373a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821036"
---
# <a name="sysdm_os_process_memory-transact-sql"></a>sys.dm_os_process_memory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  В большинстве случаев можно управлять памятью, выделяемой процессу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с помощью диалоговых окон, позволяющих отслеживать распределение памяти и вести ее учет. Однако распределение памяти может осуществляться в адресном пространстве [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] путем вызова внутренних процедур управления памятью. Значения получаются через вызовы к базовой операционной системе. Они не управляются методами, внутренними с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , за исключением случаев, когда он корректируется на блокировку или большое выделение страниц.  
  
 Все возвращаемые значения объемов памяти отображаются в килобайтах (КБ). Столбец **total_virtual_address_space_reserved_kb** является дубликатом **virtual_memory_in_bytes** из **sys. dm_os_sys_info**.  
  
 Следующая таблица содержит полную информацию об адресном пространстве процессов.  
  
> [!NOTE]  
>  Чтобы вызвать эту функцию из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , используйте имя **sys. dm_pdw_nodes_os_process_memory**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**physical_memory_in_use_kb**|**bigint**|Указывает суммарный объем рабочего множества процессов в КБ (по данным операционной системы) и отслеживаемой памяти, выделенной с помощью больших страниц и API-интерфейсов расширений AWE. Не допускает значения NULL.|  
|**large_page_allocations_kb**|**bigint**|Указывает физическую память, выделенную с помощью API-интерфейсов больших страниц. Не допускает значения NULL.|  
|**locked_page_allocations_kb**|**bigint**|Указывает страницы памяти, заблокированные в памяти. Не допускает значения NULL.|  
|**total_virtual_address_space_kb**|**bigint**|Указывает общий объем виртуального адресного пространства в пользовательском режиме. Не допускает значения NULL.|  
|**virtual_address_space_reserved_kb**|**bigint**|Указывает общий объем виртуального адресного пространства, зарезервированного процессом. Не допускает значения NULL.|  
|**virtual_address_space_committed_kb**|**bigint**|Указывает объем зарезервированного виртуального адресного пространства, зафиксированного или сопоставленного с физическими страницами. Не допускает значения NULL.|  
|**virtual_address_space_available_kb**|**bigint**|Указывает объем виртуального адресного пространства, свободного в данный момент. Не допускает значения NULL.<br /><br /> **Примечание.** Свободные регионы, размер которых меньше, чем степень гранулярности распределения, могут существовать. Эти области недоступны для выделений.|  
|**page_fault_count**|**bigint**|Указывает количество ошибок страниц, вызванных процессом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значения NULL.|  
|**memory_utilization_percentage**|**int**|Указывает долю зафиксированной памяти в рабочем множестве, в процентах. Не допускает значения NULL.|  
|**available_commit_limit_kb**|**bigint**|Указывает объем памяти, доступной для размещения процесса. Не допускает значения NULL.|  
|**process_physical_memory_low**|**bit**|Указывает, что процесс обрабатывает уведомление о нехватке физической памяти. Не допускает значения NULL.|  
|**process_virtual_memory_low**|**bit**|Указывает, что обнаружена нехватка виртуальной памяти. Не допускает значения NULL.|  
|**pdw_node_id**|**int**|**Применимо к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ,[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор узла, на котором находится данное распределение.|  
  
## <a name="permissions"></a>Разрешения  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуется разрешение VIEW SERVER STATE на сервере.  
  
В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server динамические административные представления, связанные с операционной системой &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


