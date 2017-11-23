---
title: "sys.dm_db_missing_index_columns (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_missing_index_columns_TSQL
- sys.dm_db_missing_index_columns_TSQL
- sys.dm_db_missing_index_columns
- dm_db_missing_index_columns
dev_langs: TSQL
helpviewer_keywords:
- sys.dm_db_missing_index_columns dynamic management function
- missing indexes feature [SQL Server], sys.dm_db_missing_index_columns dynamic management function
ms.assetid: 3b24e5ed-0c79-47e5-805c-a0902d0aeb86
caps.latest.revision: "40"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6f2f358532d43453242fea591ab9ac12024230f2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbmissingindexcolumns-transact-sql"></a>sys.dm_db_missing_index_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает информацию о столбцах таблицы в базе данных, для которых отсутствует индекс (исключая пространственные индексы). **sys.dm_db_missing_index_columns** является функцией динамического управления.  

## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_db_missing_index_columns(index_handle)  
```  
  
## <a name="arguments"></a>Аргументы  
 *index_handle*  
 Целочисленное значение, уникальным образом идентифицирующее отсутствующий индекс. Его можно получить из следующих объектов DMO.  
  
 [sys.dm_db_missing_index_details &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)  
  
 [sys.dm_db_missing_index_groups &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**Идентификатор column_id**|**int**|Идентификатор столбца.|  
|**column_name**|**sysname**|Имя столбца таблицы.|  
|**column_usage**|**varchar(20)**|Способ использования столбца запросом. Ниже приведены возможные значения и их описания.<br /><br /> РАВЕНСТВО: Столбец участвует в предикате, выражающем равенство, в формате: <br />                        *Таблица.столбец* = *constant_value*<br /><br /> НЕРАВЕНСТВО: Столбец участвует в предикате, выражающем неравенство, например предикат в формате: *таблица.столбец* > *constant_value*. Любой оператор сравнения, кроме «=», выражает неравенство.<br /><br /> ВКЛЮЧИТЬ: Столбец не используется для вычисления предиката, но использовать по другой причине, например, для выполнения запроса.|  
  
## <a name="remarks"></a>Замечания  
 Сведения, возвращаемые функцией **sys.dm_db_missing_index_columns** обновляется, когда запрос оптимизирован оптимизатором запросов и не сохраняется. Сведения об отсутствующих индексах хранятся только до перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Администраторы базы данных должны периодически делать резервные копии сведений об отсутствующих индексах, чтобы сохранить их после перезагрузки сервера.  
  
## <a name="transaction-consistency"></a>Согласованность транзакций  
 Если транзакция создает или удаляет таблицу, то строки, содержащие сведения отсутствующих индексов об удаленных объектах, удаляются из данного объекта DMO, сохраняя согласованность транзакций.  
  
## <a name="permissions"></a>Permissions  
 Пользователям необходимо предоставить разрешение VIEW SERVER STATE или любое разрешение, которое подразумевает разрешение VIEW SERVER STATE, чтобы выполнить запрос к этой функции динамического управления.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выполняется запрос к таблице `Address`, а затем выполняется запрос с использованием динамического административного представления `sys.dm_db_missing_index_columns` для возврата столбцов таблицы, отсутствующих в индексе.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode  
FROM Person.Address  
WHERE StateProvinceID = 9;  
GO  
SELECT mig.*, statement AS table_name,  
    column_id, column_name, column_usage  
FROM sys.dm_db_missing_index_details AS mid  
CROSS APPLY sys.dm_db_missing_index_columns (mid.index_handle)  
INNER JOIN sys.dm_db_missing_index_groups AS mig ON mig.index_handle = mid.index_handle  
ORDER BY mig.index_group_handle, mig.index_handle, column_id;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_db_missing_index_details &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sys.dm_db_missing_index_groups &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
