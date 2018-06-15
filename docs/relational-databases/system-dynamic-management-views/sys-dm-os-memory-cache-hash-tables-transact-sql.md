---
title: кэшей (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_hash_tables_TSQL
- sys.dm_os_memory_cache_hash_tables
- dm_os_memory_cache_hash_tables
- dm_os_memory_cache_hash_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_hash_tables dynamic management view
ms.assetid: 68b94f35-8f80-4d2b-bcde-7a21934219af
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 50e261fb0c53da8caf9f9b41d15d0f96dc7a41e4
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34467780"
---
# <a name="sysdmosmemorycachehashtables-transact-sql"></a>sys.dm_os_memory_cache_hash_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает строку для каждого активного кэша в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_memory_cache_hash_tables**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|Адрес (первичный ключ) записи кэша. Не допускает значение NULL.|  
|**name**|**nvarchar(256)**|Имя кэша. Не допускает значение NULL.|  
|**type**|**nvarchar(60)**|Тип кэша. Не допускает значение NULL.|  
|**table_level**|**int**|Номер таблицы кэша. Частичный кэш может содержать множество хэшированных таблиц, которые соответствуют разным хэш-функциям. Не допускает значение NULL.|  
|**buckets_count**|**int**|Количество сегментов в хэш-таблице. Не допускает значение NULL.|  
|**buckets_in_use_count**|**int**|Количество сегментов, используемых в настоящий момент. Не допускает значение NULL.|  
|**buckets_min_length**|**int**|Минимальное количество вхождений кэша в сегменте. Не допускает значение NULL.|  
|**buckets_max_length**|**int**|Максимальное количество вхождений кэша в сегменте. Не допускает значение NULL.|  
|**buckets_avg_length**|**int**|Среднее количество вхождений кэша в каждом сегменте. Не допускает значение NULL.|  
|**buckets_max_length_ever**|**int**|Максимальное количество кэшированных записей в сегменте хэша для этой таблицы хэша с момента запуска сервера. Не допускает значение NULL.|  
|**hits_count**|**bigint**|Количество попаданий в кэш. Не допускает значение NULL.|  
|**misses_count**|**bigint**|Количество неудачных обращений к кэшу. Не допускает значение NULL.|  
|**buckets_avg_scan_hit_length**|**int**|Среднее количество проверенных записей в сегменте перед нахождением искомого элемента. Не допускает значение NULL.|  
|**buckets_avg_scan_miss_length**|**int**|Среднее количество проверенных записей в сегменте перед неудачным завершением поиска. Не допускает значение NULL.|  
|**pdw_node_id**|**int**|Идентификатор для узла, это распределение.<br /><br /> **Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>Разрешения 

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="see-also"></a>См. также  
 
  [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


