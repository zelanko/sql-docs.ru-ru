---
description: sys. pdw_database_mappings (Transact-SQL)
title: sys. pdw_database_mappings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4ae2c71e-dd56-41ea-a16b-64936175b459
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c406f00d6ee9848ab5f09631d77436ef6b6dbddf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490298"
---
# <a name="syspdw_database_mappings-transact-sql"></a>sys. pdw_database_mappings (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Сопоставляет **database_id**s из баз данных с физическим именем, используемым на вычисленных узлах, и предоставляет **идентификатор субъекта** владельца базы данных в системе. Присоедините **sys. pdw_database_mappings** к **sys. databases** и **sys. pdw_nodes_pdw_physical_databases**.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|physical_name|**nvarchar (36)**|Физическое имя базы данных на вычисленных узлах.<br /><br /> **physical_name** и **database_id** формируют ключ для этого представления.||  
|database_id|**int**|Идентификатор объекта для базы данных. См. раздел [sys. databases &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).<br /><br /> **physical_name** и **database_id** формируют ключ для этого представления.||  
  
## <a name="examples-sspdw"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример соединяет sys. pdw_database_mappings с другими системными таблицами, чтобы продемонстрировать, как сопоставляются базы данных.  
  
```  
SELECT DB.database_id, DB.name, Map.*, Phys.*   
FROM sys.databases AS DB  
JOIN sys.pdw_database_mappings AS Map  
    ON DB.database_id = Map.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS Phys  
    ON Map.physical_name = Phys.physical_name  
ORDER BY DB.database_id, Phys.pdw_node_id;  
```  
  
## <a name="see-also"></a>См. также  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
 [sys. pdw_index_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)   
 [sys. pdw_table_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [sys. pdw_nodes_pdw_physical_databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-pdw-physical-databases-transact-sql.md)  
  
  

