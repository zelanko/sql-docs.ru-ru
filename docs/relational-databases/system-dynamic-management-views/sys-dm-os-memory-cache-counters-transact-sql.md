---
title: sys.dm_os_memory_cache_counters (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_counters_TSQL
- dm_os_memory_cache_counters_TSQL
- sys.dm_os_memory_cache_counters
- dm_os_memory_cache_counters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_counters dynamic management view
ms.assetid: ca7bd036-d661-4c17-b00a-e1a975bd8932
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c5a513e851ed7a521009d39c927d2e5f94335994
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2018
---
# <a name="sysdmosmemorycachecounters-transact-sql"></a>sys.dm_os_memory_cache_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает моментальный снимок исправности кэша в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **sys.dm_os_memory_cache_counters** предоставляет во время выполнения сведения о выделенных записях кэша, их использовании и источнике памяти для записей кэша.  
  
> **Примечание:** вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_memory_cache_counters**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|Указывает адрес (первичный ключ) счетчиков, связанных с указанным кэшем. Не допускает значение NULL.|  
|**name**|**nvarchar(256)**|Указывает имя кэша. Не допускает значение NULL.|  
|**type**|**nvarchar(60)**|Указывает тип кэша, связанного с этой записью. Не допускает значение NULL.|  
|**single_pages_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Размер одной выделенной страницы памяти в килобайтах. Объем памяти, выделенный с помощью одностраничного блока распределения. Это относится к 8-килобайтным страницам, взятым прямо из буферного пула для этого кэша. Не допускает значение NULL.|  
|**pages_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает объем (в килобайтах) памяти, выделенной в кэш. Не допускает значение NULL.|  
|**multi_pages_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Размер выделенной многостраничной памяти в килобайтах. Это объем памяти, выделенной с помощью многостраничного блока распределения узла памяти. Эта память выделена вне буферного пула и использует преимущества виртуального блока распределения узлов памяти. Не допускает значение NULL.|  
|**pages_in_use_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает объем (в килобайтах) памяти, выделенной и используемой в кэше. Допускает значение NULL.  Значения для объектов типа `USERSTORE_<*>` не отслеживаются.  Для них выводится значение NULL.|  
|**single_pages_in_use_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Размер используемой одностраничной памяти в килобайтах. Допускает значение NULL. Эти сведения не отслеживаются для объектов типа USERSTORE_\<* > эти значения будут равны NULL.|  
|**multi_pages_in_use_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Размер используемой многостраничной памяти в килобайтах. Допускает значение NULL. Эти сведения не отслеживаются для объектов типа USERSTORE_\<* >, и эти значения будут равны NULL.|  
|**entries_count**|**bigint**|Указывает количество записей в кэше. Не допускает значение NULL.|  
|**entries_in_use_count**|**bigint**|Указывает количество записей в используемом кэше. Не допускает значение NULL.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения 

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="see-also"></a>См. также  
  [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


