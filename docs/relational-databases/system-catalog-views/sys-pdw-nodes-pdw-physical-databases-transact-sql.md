---
description: sys.pdw_nodes_pdw_physical_databases (Transact-SQL)
title: sys.pdw_nodes_pdw_physical_databases (Transact-SQL)
ms.custom: seo-dt-2019
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
ms.openlocfilehash: 3f4b29984f962f2ec4f542a57cd604c619a78c6a
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036717"
---
# <a name="syspdw_nodes_pdw_physical_databases-transact-sql"></a>sys.pdw_nodes_pdw_physical_databases (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Содержит по одной строке для каждой физической базы данных на кластерном узле. Статистическая обработка физической информации базы данных для получения подробных сведений о базах данных. Чтобы объединить сведения, присоедините `sys.pdw_nodes_pdw_physical_databases` к `sys.pdw_database_mappings` `sys.databases` таблицам и.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор объекта для базы данных. Обратите внимание, что это значение не совпадает с database_id в представлении [sys. databases &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) .|  
|physical_name|**sysname**|Физическое имя базы данных на узлах оболочки или вычислений. Это значение совпадает со значением столбца physical_name в [sys.pdw_database_mappings &#40;представлении&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md) .|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.|  
  
## <a name="examples-sspdw"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-returning"></a>A. Возвращаются  
 Следующий запрос возвращает имя и идентификатор каждой базы данных в Master, а также соответствующее имя базы данных на каждом кластерном узле.  
  
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
  
### <a name="b-using-syspdw_nodes_pdw_physical_databases-to-gather-detailed-object-information"></a>Б. Использование sys.pdw_nodes_pdw_physical_databases для сбора подробных сведений об объекте  
 Следующий запрос показывает сведения о индексах и содержит полезные сведения о базе данных, которые объекты принадлежат к объектам в базе данных.  
  
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
  
### <a name="c-using-syspdw_nodes_pdw_physical_databases-to-determine-the-encryption-state"></a>В. Определение состояния шифрования с помощью sys.pdw_nodes_pdw_physical_databases  
 Следующий запрос обеспечивает состояние шифрования базы данных AdventureWorksPDW2012.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Представления каталога Azure Synapse Analytics и Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.pdw_database_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
  

