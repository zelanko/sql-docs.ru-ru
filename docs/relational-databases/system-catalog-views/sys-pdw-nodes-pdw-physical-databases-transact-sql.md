---
title: sys.pdw_nodes_pdw_physical_databases (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 70e0939d-4d97-4ae0-ba16-934e0a80e718
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3dd4551d2dac629912eb4fe799d6a9e58ec1792b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001132"
---
# <a name="syspdwnodespdwphysicaldatabases-transact-sql"></a>sys.pdw_nodes_pdw_physical_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит по строке для каждой физической базы данных на вычислительном узле. Статистические сведения о физической базы данных, чтобы получить подробные сведения о базах данных. Для объединения данных, присоединить `sys.pdw_nodes_pdw_physical_databases` для `sys.pdw_database_mappings` и `sys.databases` таблицы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор объекта для базы данных. Обратите внимание, что это значение не то же, что database_id в [sys.databases &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления.|  
|physical_name|**sysname**|Физическое имя базы данных на оболочки/вычислительных узлов. Это значение совпадает с значение в столбце physical_name [sys.pdw_database_mappings &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md) представления.|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.|  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-returning"></a>A. Возврат  
 Следующий запрос возвращает имя и идентификатор каждой базы данных в master и имя соответствующей базы данных на каждом вычислительном узле.  
  
```  
SELECT D.database_id AS DBID_in_master, D.name AS UserDatabaseName,   
PD.pdw_node_id AS NodeID, DM.physical_name AS PhysDBName   
FROM sys.databases AS D  
JOIN sys.pdw_database_mappings AS DM  
    ON D.database_id = DM.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS PD  
    ON DM.physical_name = PD.physical_name  
ORDER BY D.database_id, PD.pdw_node_ID;  
```  
  
### <a name="b-using-syspdwnodespdwphysicaldatabases-to-gather-detailed-object-information"></a>Б. С помощью sys.pdw_nodes_pdw_physical_databases для сбора информации подробные объекта  
 Следующий запрос отображает сведения об индексах и включает полезные сведения о базе данных, что объекты принадлежат объекты в базе данных.  
  
```  
SELECT D.name AS UserDatabaseName, D.database_id AS DBIDinMaster,  
DM.physical_name AS PhysDBName, PD.pdw_node_id AS NodeID,   
IU.object_id, IU.index_id, IU.user_seeks, IU.user_scans, IU.user_lookups, IU.user_updates  
FROM sys.databases AS D  
JOIN sys.pdw_database_mappings AS DM  
    ON D.database_id = DM.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS PD  
    ON DM.physical_name = PD.physical_name  
JOIN sys.dm_pdw_nodes_db_index_usage_stats AS IU  
    ON PD.database_id = IU.database_id  
ORDER BY D.database_id, IU.object_id, IU.index_id, PD.pdw_node_ID;  
```  
  
### <a name="c-using-syspdwnodespdwphysicaldatabases-to-determine-the-encryption-state"></a>В. С помощью sys.pdw_nodes_pdw_physical_databases определение состояния шифрования  
 Следующий запрос предоставляет состояние шифрования базы данных AdventureWorksPDW2012.  
  
```  
WITH dek_encryption_state AS   
(  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id, encryption_state  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
        INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
            ON dek.database_id = node_db_map.database_id AND dek.pdw_node_id = node_db_map.pdw_node_id  
        LEFT JOIN sys.pdw_database_mappings AS db_map  
            ON node_db_map .physical_name = db_map.physical_name  
        INNER JOIN sys.dm_pdw_nodes AS nodes  
            ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
)  
SELECT TOP 1 encryption_state  
       FROM  dek_encryption_state  
       WHERE dek_encryption_state.database_id = DB_ID('AdventureWorksPDW2012 ')  
       ORDER BY (CASE encryption_state WHEN 3 THEN -1 ELSE encryption_state END) DESC;  
```  
  
## <a name="see-also"></a>См. также  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.pdw_database_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
  

