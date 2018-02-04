---
title: "sys.dm_os_memory_cache_clock_hands (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 12/21/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_clock_hands_TSQL
- dm_os_memory_cache_clock_hands
- dm_os_memory_cache_clock_hands_TSQL
- sys.dm_os_memory_cache_clock_hands
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_clock_hands dynamic management view
ms.assetid: 0660eddc-691c-425f-9d43-71151d644de7
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 08e181d6f4735a8977d8af4fb226d7f532a4e88d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmosmemorycacheclockhands-transact-sql"></a>sys.dm_os_memory_cache_clock_hands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает состояние каждой стрелки указанных часов кэша.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_memory_cache_clock_hands**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|Адрес кэша, связанного с часами. Не допускает значение NULL.|  
|**name**|**nvarchar(256)**|Имя кэша. Не допускает значение NULL.|  
|**type**|**nvarchar(60)**|Тип кэша. Допускается наличие нескольких экземпляров кэша одного типа. Не допускает значение NULL.|  
|**clock_hand**|**nvarchar(60)**|Тип стрелки. Возможны следующие варианты.<br /><br /> External<br /><br /> Внутренние<br /><br /> Не допускает значение NULL.|  
|**clock_status**|**nvarchar(60)**|Состояние часов. Возможны следующие варианты.<br /><br /> Приостановлена<br /><br /> Запущен<br /><br /> Не допускает значение NULL.|  
|**rounds_count**|**bigint**|Число проходов по кэшу для удаления элементов. Не допускает значение NULL.|  
|**removed_all_rounds_count**|**bigint**|Число элементов, удаленных при всех проходах. Не допускает значение NULL.|  
|**updated_last_round_count**|**bigint**|Число элементов, обновленных во время последнего прохода. Не допускает значение NULL.|  
|**removed_last_round_count**|**bigint**|Число элементов, удаленных во время последнего прохода. Не допускает значение NULL.|  
|**last_tick_time**|**bigint**|Время последнего перемещения стрелки часов (в миллисекундах). Не допускает значение NULL.|  
|**round_start_time**|**bigint**|Время предыдущего прохода (в миллисекундах). Не допускает значение NULL.|  
|**last_round_start_time**|**bigint**|Общее время выполнения предыдущего цикла часов (в миллисекундах). Не допускает значение NULL.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.    
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранятся в памяти в структуру, которая называется кэшем памяти. В качестве сведений, хранящихся в этом кэше, могут выступать данные, индексные записи, скомпилированные планы выполнения процедур и множество других типов сведений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы избежать повторного создания сведений, они извлекаются из кэша памяти возможное число раз и обычно удаляются из кэша в случае их сильного устаревания или в том случае, если область памяти требуется для записи новых данных. Процесс, который удаляет устаревшие сведения из памяти, называется «чистильщиком памяти». Чистильщик памяти используется регулярно, но не непрерывно. Очисткой кэша памяти управляет временной алгоритм. Каждый таймер времени временного алгоритма может управлять несколькими чистильщиками памяти, которые называются «руками». Рука таймера чистильщика времени — это текущее место расположения одной из рук чистильщика памяти.  

## <a name="see-also"></a>См. также  
 [Относящиеся к операционной системе SQL Server динамические административные представления &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)    
 [sys.dm_os_memory_cache_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md)
  

