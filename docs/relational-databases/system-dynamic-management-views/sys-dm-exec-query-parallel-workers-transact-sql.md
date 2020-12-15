---
description: sys.dm_exec_query_parallel_workers (Transact-SQL)
title: sys.dm_exec_query_parallel_workers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_parallel_workers_TSQL
- dm_exec_query_parallel_workers
- sys.dm_exec_query_parallel_workers_TSQL
- sys.dm_exec_query_parallel_workers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_parallel_workers dynamic management view
ms.assetid: 1d72cef1-22d8-4ae0-91db-6694fe918c9f
author: pelopes
ms.author: pelopes
manager: ajayj
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 30ea6f1642da78754560b26a8772c33ab341d2b4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97477245"
---
# <a name="sysdm_exec_query_parallel_workers-transact-sql"></a>sys.dm_exec_query_parallel_workers (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa-pdw.md)]

  Возвращает сведения о доступности рабочей роли для каждого узла.  
  
|Имя|Тип данных|Описание|  
|----------|---------------|-----------------|  
|**node_id**|**int**|Идентификатор узла NUMA.|  
|**scheduler_count**|**int**|Число планировщиков на этом узле.|  
|**max_worker_count**|**int**|Максимальное число рабочих процессов для параллельных запросов.|  
|**reserved_worker_count**|**int**|Число рабочих ролей, зарезервированных параллельными запросами, плюс количество основных рабочих процессов, используемых всеми запросами.| 
|**free_worker_count**|**int**|Число рабочих ролей, доступных для задач.<br /><br />**Примечание.** каждый входящий запрос использует по крайней мере 1 рабочую роль, вычитаемую из числа свободных рабочих ролей.  Возможно, количество свободных рабочих ролей может быть отрицательным числом на сильно загруженном сервере.| 
|**used_worker_count**|**int**|Число рабочих ролей, используемых параллельными запросами.|  
  
## <a name="permissions"></a>Разрешения  

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] необходимо `VIEW SERVER STATE` разрешение.   
В базах данных SQL Basic, S0 и S1, а также для баз данных в эластичных пулах `Server admin` `Azure Active Directory admin` требуется учетная запись или. Для всех остальных целей службы базы данных SQL `VIEW DATABASE STATE` разрешение требуется в базе данных.   
 
## <a name="examples"></a>Примеры  
  
### <a name="a-viewing-current-parallel-worker-availability"></a>A. Просмотр текущей доступности параллельной рабочей роли  

```sql 
SELECT * FROM sys.dm_exec_query_parallel_workers;  
```  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)
