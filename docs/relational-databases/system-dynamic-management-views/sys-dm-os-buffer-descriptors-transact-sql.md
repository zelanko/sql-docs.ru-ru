---
title: sys.dm_os_buffer_descriptors (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_buffer_descriptors_TSQL
- dm_os_buffer_descriptors_TSQL
- sys.dm_os_buffer_descriptors
- dm_os_buffer_descriptors
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_buffer_descriptors dynamic management view
ms.assetid: 012aab95-8888-4f35-9ea3-b5dff6e3f60f
caps.latest.revision: 48
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3bae01f30cf7b6af860004f69effb4df44cf3c8b
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34465820"
---
# <a name="sysdmosbufferdescriptors-transact-sql"></a>sys.dm_os_buffer_descriptors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения обо всех страницах данных, расположенных в данный момент в буферном пуле [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это представление может использоваться, чтобы определить распределение страниц баз данных в буферном пуле в соответствии с базой данных, объектом или типом. В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] это динамическое административное представление также возвращает сведения о страницах данных в файле расширения буферного пула. Дополнительные сведения см. в разделе [расширение буферного пула](../../database-engine/configure-windows/buffer-pool-extension.md).  
  
 При считывании страницы данных с диска она копируется в буферный пул [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и кэшируется для повторного использования. Каждая страница данных в кэше имеет один дескриптор буфера. Дескрипторы буфера уникально идентифицируют каждую страницу данных, кэшируемую в данный момент в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. представление sys.dm_os_buffer_descriptors возвращает страницы в кэше для всех пользовательских и системных баз данных. В их число входят страницы, связанные с базой данных Resource.  
  
> **Примечание:** вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_buffer_descriptors**.  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Идентификатор базы данных, связанный со страницей в буферном пуле. Допускает значение NULL.|  
|file_id|**int**|Идентификатор файла, хранящего постоянный образ страницы. Допускает значение NULL.|  
|page_id|**int**|Идентификатор страницы в файле. Допускает значение NULL.|  
|page_level|**int**|Индексный уровень страницы. Допускает значение NULL.|  
|allocation_unit_id|**bigint**|Идентификатор единицы распределения страницы. Это значение может быть использовано для соединения sys.allocation_units. Допускает значение NULL.|  
|page_type|**nvarchar(60)**|Тип страницы, например: страница данных или страница индекса. Допускает значение NULL.|  
|row_count|**int**|Количество строк на странице. Допускает значение NULL.|  
|free_space_in_bytes|**int**|Объем доступного свободного места, в байтах, на странице. Допускает значение NULL.|  
|is_modified|**бит**|1 = страница была изменена после того, как она была считана с диска. Допускает значение NULL.|  
|numa_node|**int**|Узел с неоднородным доступом к памяти для буфера. Допускает значение NULL.|  
|read_microsec|**bigint**|Фактическое время (в миллисекундах), необходимое для считывания страницы в буфер. Счетчик сбрасывается, если буфер используется повторно. Допускает значение NULL.|  
|is_in_bpool_extension|**бит**|1 = страница находится в расширении буферного пула. Допускает значение NULL.|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
   
## <a name="remarks"></a>Примечания  
 представление sys.dm_os_buffer_descriptors возвращает страницы, которые используются в базе данных ресурсов. оно не возвращает сведения о свободных или заимствованных страницах, а также о страницах, в которых возникли ошибки при чтении.  
  
|От|Чтобы|В|Связь|  
|----------|--------|--------|------------------|  
|sys.dm_os_buffer_descriptors|sys.databases|database_id|«многие к одному»|  
|sys.dm_os_buffer_descriptors|\<UserDB >. sys.allocation_units|allocation_unit_id|«многие к одному»|  
|sys.dm_os_buffer_descriptors|\<UserDB >. sys.database_files|file_id|«многие к одному»|  
|sys.dm_os_buffer_descriptors|sys.dm_os_buffer_pool_extension_configuration|file_id|«многие к одному»|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-cached-page-count-for-each-database"></a>A. Получение количества страниц в кэше для каждой базы данных  
 Следующий пример возвращает количество страниц в кэше, загруженных для каждой базы данных.  
  
```  
SELECT COUNT(*)AS cached_pages_count  
    ,CASE database_id   
        WHEN 32767 THEN 'ResourceDb'   
        ELSE db_name(database_id)   
        END AS database_name  
FROM sys.dm_os_buffer_descriptors  
GROUP BY DB_NAME(database_id) ,database_id  
ORDER BY cached_pages_count DESC;  
```  
  
### <a name="b-returning-cached-page-count-for-each-object-in-the-current-database"></a>Б. Получение количества страниц в кэше для каждого объекта в текущей базе данных  
 Следующий пример возвращает количество страниц в кэше, загруженных для каждого объекта в текущей базе данных.  
  
```  
SELECT COUNT(*)AS cached_pages_count   
    ,name ,index_id   
FROM sys.dm_os_buffer_descriptors AS bd   
    INNER JOIN   
    (  
        SELECT object_name(object_id) AS name   
            ,index_id ,allocation_unit_id  
        FROM sys.allocation_units AS au  
            INNER JOIN sys.partitions AS p   
                ON au.container_id = p.hobt_id   
                    AND (au.type = 1 OR au.type = 3)  
        UNION ALL  
        SELECT object_name(object_id) AS name     
            ,index_id, allocation_unit_id  
        FROM sys.allocation_units AS au  
            INNER JOIN sys.partitions AS p   
                ON au.container_id = p.partition_id   
                    AND au.type = 2  
    ) AS obj   
        ON bd.allocation_unit_id = obj.allocation_unit_id  
WHERE database_id = DB_ID()  
GROUP BY name, index_id   
ORDER BY cached_pages_count DESC;  
```  
  
## <a name="see-also"></a>См. также  
 [sys.allocation_units (Transact-SQL)](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 
 [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [База данных Resource](../../relational-databases/databases/resource-database.md)   
 [sys.dm_os_buffer_pool_extension_configuration & #40; Transact-SQL & #41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-buffer-pool-extension-configuration-transact-sql.md)  
  
  


