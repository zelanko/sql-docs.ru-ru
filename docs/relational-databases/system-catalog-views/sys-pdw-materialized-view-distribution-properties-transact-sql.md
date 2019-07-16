---
title: sys.pdw_materialized_view_distribution_properties (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: XiaoyuL-Preview
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 2509bdbe2510c78dbb14b59499f2b345680fd3e0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059419"
---
# <a name="syspdwmaterializedviewdistributionproperties-transact-sql-preview"></a>sys.pdw_materialized_view_distribution_properties (Transact-SQL) (Предварительная версия)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Отображает сведения распространения материализованных представлений.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------| 
|object_id|**int**|Идентификатор материализованное представление, для которых тебя были указаны свойства.| 
|distribution_policy |**tinyint**|2 = HASH</br>4 = ROUND_ROBIN|  
|distribution_policy_desc |**nvarchar(60)**|ХЭШ-КОД, ROUND_ROBIN|  
 
## <a name="permissions"></a>Разрешения

Необходимо разрешение VIEW DATABASE STATE.
 
## <a name="see-also"></a>См. также

[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
[System views supported in Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)  (Системные представления, поддерживаемые в службе "Хранилище данных SQL Azure")  
[T-SQL statements supported in Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements) (Инструкции Т-SQL, поддерживаемые в службе "Хранилище данных SQL Azure")
