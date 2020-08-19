---
description: sys.dm_db_missing_index_details (Transact-SQL)
title: sys. dm_db_missing_index_details (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2229cbb859443a8b3669aa1b0b819af30d9893e6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490023"
---
# <a name="sysdm_db_missing_index_details-transact-sql"></a>sys.dm_db_missing_index_details (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает подробные сведения об отсутствующих индексах, за исключением пространственных индексов.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Во избежание раскрытия этой информации все строки, содержащие данные, не принадлежащие подключенному клиенту, отфильтровываются.  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**index_handle**|**int**|Идентифицирует специфический отсутствующий индекс. Этот идентификатор уникален для сервера. **index_handle** является ключом этой таблицы.|  
|**database_id**|**smallint**|Идентифицирует базу данных, в которой находится таблица с отсутствующим индексом.|  
|**object_id**|**int**|Идентифицирует таблицу, в которой отсутствует индекс.|  
|**equality_columns**|**nvarchar(4000)**|Список столбцов с разделителями-запятыми, соответствующих предикатам равенства в форме:<br /><br /> *таблица. столбец*  = *constant_value*|  
|**inequality_columns**|**nvarchar(4000)**|Список столбцов с разделителями-запятыми, который соответствует предикатам неравенства, например предикатам в форме:<br /><br /> *таблица. столбец*  >  *constant_value*<br /><br /> Любой оператор сравнения, кроме «=», выражает неравенство.|  
|**included_columns**|**nvarchar(4000)**|Список столбцов с разделителями-запятыми, необходимых в качестве столбцов для запроса. Дополнительные сведения о охватывающих или включаемых столбцах см. в разделе [Создание индексов с включением столбцов](../../relational-databases/indexes/create-indexes-with-included-columns.md).<br /><br /> Для оптимизированных для памяти индексов (хэш-и оптимизированных для памяти некластеризованных) игнорируйте **included_columns**. Все столбцы таблицы включаются в каждый индекс с оптимизацией для памяти.|  
|**инструкция**|**nvarchar(4000)**|Имя таблицы, в которой отсутствует индекс.|  
  
## <a name="remarks"></a>Remarks  
 Сведения, возвращенные представлением **sys.dm_db_missing_index_details**, будут обновленными, если запрос оптимизирован оптимизатором запросов и не является сохраненным. Сведения об отсутствующих индексах хранятся только до перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Администраторы базы данных должны периодически делать резервные копии сведений об отсутствующих индексах, чтобы сохранить их после перезагрузки сервера.  
  
 Чтобы определить, в какие группы входит отсутствующий индекс, можно выполнить запрос к динамическому административному представлению **sys.dm_db_missing_index_groups**, объединив его по эквивалентности с представлением **sys.dm_db_missing_index_details**, основанным на столбце **index_handle**.  

  >[!NOTE]
  >Результирующий набор для этого динамического административного представления ограничен 600 строк. Каждая строка содержит один отсутствующий индекс. Если у вас больше 600 отсутствующих индексов, следует устранить существующие отсутствующие индексы, чтобы можно было просмотреть новые. 
  
## <a name="using-missing-index-information-in-create-index-statements"></a>Использование сведений об отсутствующих индексах в инструкциях CREATE INDEX  
 Чтобы преобразовать сведения, возвращаемые **sys. dm_db_missing_index_details** , в инструкцию CREATE INDEX для оптимизированных для памяти и дисковых индексов, столбцы равенства должны быть размещены перед столбцами неравенства, и вместе они должны сделать ключ индекса. Включенные столбцы должны быть добавлены в инструкцию CREATE INDEX с помощью предложения INCLUDE. Чтобы определить эффективный порядок столбцов равенства, расположите их на основе их выборности, перечисляя наиболее выбираемые столбцы первыми (крайние левые в списке столбцов).  
  
 Дополнительные сведения об индексах, оптимизированных для памяти, см. в разделе [индексы для таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  
  
## <a name="transaction-consistency"></a>Согласованность транзакций  
 Если транзакция создает или удаляет таблицу, то строки, содержащие сведения отсутствующих индексов об удаленных объектах, удаляются из данного объекта DMO, сохраняя согласованность транзакций.  
  
## <a name="permissions"></a>Разрешения

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется  **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   

## <a name="see-also"></a>См. также:  
 [sys. dm_db_missing_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys. dm_db_missing_index_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [sys. dm_db_missing_index_group_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
