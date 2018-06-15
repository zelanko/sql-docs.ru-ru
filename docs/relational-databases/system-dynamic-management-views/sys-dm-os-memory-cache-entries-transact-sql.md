---
title: sys.dm_os_memory_cache_entries (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_memory_cache_entries
- sys.dm_os_memory_cache_entries
- dm_os_memory_cache_entries_TSQL
- sys.dm_os_memory_cache_entries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_entries dynamic management view
ms.assetid: dd32be6b-10d1-4059-b4fd-0bf817f40d54
caps.latest.revision: 39
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cb6c3adbf021eb08b8e76892217cf04c9caeafe0
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34468026"
---
# <a name="sysdmosmemorycacheentries-transact-sql"></a>sys.dm_os_memory_cache_entries (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения обо всех записях в кэше в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Используйте это представление, чтобы трассировать связь записей из кэша и ассоциированных с ними объектов. Кроме того, это представление можно использовать для получения статистики по записям в кэше.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_memory_cache_entries**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|Адрес кэша. Не допускает значение NULL.|  
|**name**|**nvarchar(256)**|Имя кэша. Не допускает значение NULL.|  
|**type**|**varchar(60)**|Тип кэша. Не допускает значение NULL.|  
|**entry_address**|**varbinary(8)**|Адрес дескриптора записи кэша. Не допускает значение NULL.|  
|**entry_data_address**|**varbinary(8)**|Адрес данных пользователя в записи кэша.<br /><br /> 0x00000000 = адрес данных записи не доступен.<br /><br /> Не допускает значение NULL.|  
|**in_use_count**|**int**|Число пользователей, одновременно использующих эту запись кэша. Не допускает значение NULL.|  
|**is_dirty**|**бит**|Указывает, помечена ли эта запись кэша для удаления. 1 — помечена для удаления. Не допускает значение NULL.|  
|**disk_ios_count**|**int**|Число операций ввода-вывода в момент создания этой записи. Не допускает значение NULL.|  
|**context_switches_count**|**int**|Число переключателей контекста в момент создания этой записи. Не допускает значение NULL.|  
|**original_cost**|**int**|Исходная стоимость записи. Это значение представляет собой приблизительное число вызванных операций ввода-вывода, стоимость инструкции ЦП и объем памяти, потребляемой каждой записью. Чем выше стоимость, тем меньше вероятность того, что элемент будет удален из кэша. Не допускает значение NULL.|  
|**current_cost**|**int**|Текущая стоимость записи кэша. Это значение обновляется в процессе очистки записи. При повторном использовании записи текущая стоимость сбрасывается на исходное значение. Не допускает значение NULL.|  
|**memory_object_address**|**varbinary(8)**|Адрес ассоциированного объекта памяти. Допускает значение NULL.|  
|**pages_allocated_count**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Количество восьмикилобайтных страниц для хранения в этой записи кэша. Не допускает значение NULL.|  
|**pages_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Объем памяти (в килобайтах), используемый этой записью кэша.  Не допускает значение NULL.|  
|**entry_data**|**nvarchar(2048)**|Сериализованное представление кэшированной записи. Эти сведения зависят от хранения кэша. Допускает значение NULL.|  
|**pool_id**|**int**|**Область применения**: начиная с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Пул ресурсов связан с записью. Допускает значение NULL.<br /><br /> не katmai|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения 

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="see-also"></a>См. также  
 
  [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


