---
title: "sys.dm_exec_query_parallel_workers (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: pelopes
ms.author: pelopes
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: 99165e38dc4f1ad0b25a754f2c0f38b4ae413e84
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
---
# <a name="sysdmexecqueryparallelworkers-transact-sql"></a>sys.dm_exec_query_parallel_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Возвращает рабочий сведений о доступности на каждом узле.  
  
|Название|Тип данных|Описание|  
|----------|---------------|-----------------|  
|**NODE_ID**|**int**|Идентификатор узла NUMA.|  
|**scheduler_count**|**int**|Количество планировщиков на данном узле.|  
|**max_worker_count**|**int**|Максимальное число рабочих процессов для параллельных запросов.|  
|**reserved_worker_count**|**int**|Число рабочих процессов, зарезервированной с помощью параллельных запросов, а также число основных рабочих процессов, используемых всеми запросами.| 
|**free_worker_count**|**int**|Количество рабочих потоков, доступных для задач.<br /><br />**Примечание:** по крайней мере 1 worker вычитается из число свободных рабочих потребляет каждого входящего запроса.  Это возможно, что число свободных рабочих может быть отрицательным числом на сильно загруженном сервере.| 
|**used_worker_count**|**int**|Число рабочих процессов, используемых параллельных запросов.|  
  
## <a name="permissions"></a>Разрешения  
 На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо разрешение VIEW SERVER STATE на сервере.  
  
 На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Premium необходимо разрешение VIEW DATABASE STATE в базе данных. На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Standard и Basic требуется [!INCLUDE[ssSDS](../../includes/sssds-md.md)] учетная запись администратора.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-viewing-current-parallel-worker-availability"></a>A. Просмотр текущего параллельных доступности  

```sql 
SELECT * FROM sys.dm_exec_query_parallel_workers;  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [&#40; динамические административные представления и функции, связанные с выполнением Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_os_workers &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)
