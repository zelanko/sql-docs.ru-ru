---
title: sys.dm_db_missing_index_details (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_details
- dm_db_missing_index_details
- sys.dm_db_missing_index_details_TSQL
- dm_db_missing_index_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- missing indexes feature [SQL Server], sys.dm_db_missing_index_details dynamic management view
- sys.dm_db_missing_index_details dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7d3b07692b4e12ab4bdd0be15566cf115ad71b76
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34465630"
---
# <a name="sysdmdbmissingindexdetails-transact-sql"></a>sys.dm_db_missing_index_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает подробные сведения об отсутствующих индексах, за исключением пространственных индексов.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Чтобы избежать предоставления этих сведений, все строки, содержащие данные, не принадлежащие к подключенному клиенту, фильтруются.  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**index_handle**|**int**|Идентифицирует специфический отсутствующий индекс. Этот идентификатор уникален для сервера. **index_handle** является ключевым для данной таблицы.|  
|**database_id**|**smallint**|Идентифицирует базу данных, в которой находится таблица с отсутствующим индексом.|  
|**object_id**|**int**|Идентифицирует таблицу, в которой отсутствует индекс.|  
|**equality_columns**|**nvarchar(4000)**|Список столбцов с разделителями-запятыми, соответствующих предикатам равенства в форме:<br /><br /> *table.column* =*constant_value*|  
|**inequality_columns**|**nvarchar(4000)**|Список столбцов с разделителями-запятыми, который соответствует предикатам неравенства, например предикатам в форме:<br /><br /> *table.column* > *constant_value*<br /><br /> Любой оператор сравнения, кроме «=», выражает неравенство.|  
|**included_columns**|**nvarchar(4000)**|Список столбцов с разделителями-запятыми, необходимых в качестве столбцов для запроса. Дополнительные сведения о или включенных столбцах см. в разделе [создание индексов с включенными столбцами](../../relational-databases/indexes/create-indexes-with-included-columns.md).<br /><br /> Для индексов, оптимизированных для памяти (оба хэширования и оптимизированных для памяти некластеризованный), игнорировать **included_columns**. Все столбцы таблицы включаются в каждый индекс с оптимизацией для памяти.|  
|**инструкция**|**nvarchar(4000)**|Имя таблицы, в которой отсутствует индекс.|  
  
## <a name="remarks"></a>Примечания  
 Сведения, возвращаемые функцией **sys.dm_db_missing_index_details** обновляется, когда запрос оптимизирован оптимизатором запросов и не сохраняется. Сведения об отсутствующих индексах хранятся только до перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Администраторы базы данных должны периодически делать резервные копии сведений об отсутствующих индексах, чтобы сохранить их после перезагрузки сервера.  
  
 Чтобы определить, какие группы входит отсутствующий индекс является частью, вы можете запросить **sys.dm_db_missing_index_groups** динамическому административному представлению, объединив его с **sys.dm_db_missing_index_details**  на основе **index_handle** столбца.  
  
## <a name="using-missing-index-information-in-create-index-statements"></a>Использование сведений об отсутствующих индексах в инструкциях CREATE INDEX  
 Для преобразования сведений, возвращенных **sys.dm_db_missing_index_details** инструкции CREATE INDEX для дисковых и оптимизированных для памяти индексы, столбцы равенства должны быть помещены перед столбцами неравенства, а вместе они должны образовать индекс ключа. Включенные столбцы должны быть добавлены в инструкцию CREATE INDEX с помощью предложения INCLUDE. Чтобы определить эффективный порядок столбцов равенства, расположите их на основе их выборности, перечисляя наиболее выбираемые столбцы первыми (крайние левые в списке столбцов).  
  
 Дополнительные сведения об индексах оптимизированных для памяти см. в разделе [индексы для оптимизированных для памяти таблиц](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  
  
## <a name="transaction-consistency"></a>Согласованность транзакций  
 Если транзакция создает или удаляет таблицу, то строки, содержащие сведения отсутствующих индексов об удаленных объектах, удаляются из данного объекта DMO, сохраняя согласованность транзакций.  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="see-also"></a>См. также  
 [sys.dm_db_missing_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys.dm_db_missing_index_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
