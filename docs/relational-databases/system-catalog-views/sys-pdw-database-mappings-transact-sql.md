---
title: sys. pdw_database_mappings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/17/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4ae2c71e-dd56-41ea-a16b-64936175b459
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 46474439474f8a38ba016b16e323b0cb92afe39e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139941"
---
# <a name="syspdw_database_mappings-transact-sql"></a>sys. pdw_database_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Сопоставляет **database_id**s из баз данных с физическим именем, используемым на вычисленных узлах, и предоставляет **идентификатор субъекта** владельца базы данных в системе. Присоедините **sys. pdw_database_mappings** к **sys. databases** и **sys. pdw_nodes_pdw_physical_databases**.  
  
|Имя столбца|Тип данных|Description|Диапазонный индекс|  
|-----------------|---------------|-----------------|-----------|  
|physical_name|**nvarchar (36)**|Физическое имя базы данных на вычисленных узлах.<br /><br /> **physical_name** и **database_id** формируют ключ для этого представления.||  
|database_id|**int**|Идентификатор объекта для базы данных. См. раздел [sys. databases &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).<br /><br /> **physical_name** и **database_id** формируют ключ для этого представления.||  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
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
  
## <a name="see-also"></a>См. также:  
 [Хранилища данных SQL и представления каталога параллельных хранилищ данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys. pdw_index_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)   
 [sys. pdw_table_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [sys. pdw_nodes_pdw_physical_databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-pdw-physical-databases-transact-sql.md)  
  
  

