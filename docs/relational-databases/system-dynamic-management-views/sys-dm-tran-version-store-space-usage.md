---
title: sys.dm_tran_version_store_space_usage (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_version_store_space_usage_TSQL
- sys.dm_tran_version_store_space_usage
- dm_tran_version_store_space_usage
- dm_tran_version_store_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_version_store_space_usage dynamic management view
ms.assetid: 7ab44517-0351-4f91-bdd9-7cf940f03c51
author: savjani
ms.author: pariks
manager: ajayj
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f8ae2babba09f30b03ea512a85bdc6f06c4bf7f1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47688282"
---
# <a name="sysdmtranversionstorespaceusage-transact-sql"></a>sys.dm_tran_version_store_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-2016sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2016sp2-asdb-xxxx-xxx-md.md)]

Возвращает таблицу, отображающую общее пространство в базе данных tempdb, используемые записями хранилища версий для каждой базы данных. **sys.dm_tran_version_store_space_usage** эффективна и не сложно запустить, не осуществляет навигацию по записям хранилища отдельную версию, а возвращает сводную пространство хранилища версий, расходуется tempdb на каждую базу данных.
  
Каждая запись версии хранится в виде двоичных данных, а также некоторые сведения о состоянии и отслеживании. Как и в таблицах базы данных, записи в хранилище версий хранятся в страницах размером 8192 байта. Если размер записи превышает 8192 байта, она разбивается на две различные записи.  
  
Так как запись версии хранится в двоичном виде, не возникает проблем с разными параметрами сортировки из разных баз данных. Используйте **sys.dm_tran_version_store_space_usage** для монитора и план размер базы данных tempdb в зависимости от использованием пространства хранилища версий баз данных в экземпляре SQL Server.
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, базы данных.|  
|**reserved_page_count**|**bigint**|Общее число страниц, зарезервированных в базе данных tempdb для версии хранить записи базы данных.|  
|**reserved_space_kb**|**bigint**|Общее пространство, используемое в базе данных tempdb, в килобайтах для версии хранить записи базы данных.|  
  
## <a name="permissions"></a>Разрешения  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   

## <a name="examples"></a>Примеры  
Следующий запрос можно использовать для определения пространство, используемое в базе данных tempdb, по каждой базе данных в хранилище версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра. 
  
```sql  
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
 
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
