---
title: "sys.dm_tran_version_store_space_usage (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_version_store_space_usage_TSQL
- sys.dm_tran_version_store_space_usage
- dm_tran_version_store_space_usage
- dm_tran_version_store_space_usage_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_tran_version_store_space_usage dynamic management view
ms.assetid: 7ab44517-0351-4f91-bdd9-7cf940f03c51
caps.latest.revision: "10"
author: savjani
ms.author: pariks
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: 8488ee0a8bb823438071cb912bd56c08af640b42
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmtranversionstorespaceusage-transact-sql"></a>sys.dm_tran_version_store_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Возвращает таблицу, отображающую общее пространство в базе данных tempdb, используемые записи хранилище версий для каждой базы данных. **sys.dm_tran_version_store_space_usage** эффективна, и записывает высокопроизводительных работать, как ее не пройти хранения отдельных версий, а затем возвращает статистические версиями место хранилища, используются в базе данных tempdb на базу данных.
  
Каждая запись версии хранится в виде двоичных данных вместе с некоторыми сведениями о состоянии и отслеживании. Как и в таблицах базы данных, записи в хранилище версий хранятся в страницах размером 8192 байта. Если размер записи превышает 8192 байта, она разбивается на две различные записи.  
  
Так как запись версии хранится в двоичном виде, не возникает проблем с разными параметрами сортировки из разных баз данных. Используйте **sys.dm_tran_version_store_space_usage** отслеживание и планирование размера базы данных tempdb, в зависимости от использования пространства хранилища версии баз данных в экземпляре SQL Server.
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных из базы данных.|  
|**reserved_page_count**|**bigint**|Общее количество страниц, зарезервированных в базе данных tempdb для версии хранения записей базы данных.|  
|**reserved_space_kb**|**bigint**|Общее пространство, используемое в базе данных tempdb, в килобайтах для версии хранения записей базы данных.|  
  
## <a name="permissions"></a>Permissions  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   

## <a name="examples"></a>Примеры  
 Следующий запрос может использоваться для определения места в базе данных tempdb хранилище версий каждой базы данных в экземпляре SQL Server. 
  
```tsql  
SELECT 
  DB_NAME(database_id) as 'Database Name',
  reserved_page_count,
  reserved_space_kb 
FROM sys.dm_tran_version_store_space_usage;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Database Name            reserved_page_count reserved_space_kb  
------------------------ -------------------- -----------  
msdb                      0                    0             
AdventureWorks2016        10                   80             
AdventureWorks2016DW      0                    0             
WideWorldImporters        20                   160             
```
 
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
