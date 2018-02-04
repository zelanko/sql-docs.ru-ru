---
title: "sys.dm_repl_tranhash (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_tranhash
- sys.dm_repl_tranhash_TSQL
- dm_repl_tranhash_TSQL
- dm_repl_tranhash
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_tranhash dynamic management view
ms.assetid: 0cc52338-e805-4ed4-9835-b19bbf72448e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 34de8de4ffeb2e9cc6d2ce84ae5df81570ea9911
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmrepltranhash-transact-sql"></a>sys.dm_repl_tranhash (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о транзакции, реплицируемой в публикации транзакций.  
  
|column_name|Тип данных|description|  
|------------------|----------------|-----------------|  
|**контейнеры**|**bigint**|Количество сегментов в хэш-таблице.|  
|**hashed_trans**|**bigint**|Количество зафиксированных транзакций, реплицированных в текущем пакете.|  
|**completed_trans**|**bigint**|Количество транзакций, выполненных до настоящего момента.|  
|**compensated_trans**|**bigint**|Количество транзакций, содержащих частичный откат.|  
|**first_begin_lsn**|**nvarchar(64)**|Самый ранний начальный регистрационный номер транзакции в журнале (LSN) в текущем пакете.|  
|**last_commit_lsn**|**nvarchar(64)**|Последняя фиксация номера LSN в текущем пакете.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW DATABASE STATE в базе данных публикации на вызов **dm_repl_tranhash**.  
  
## <a name="remarks"></a>Remarks  
 Возвращаются сведения только по реплицируемым объектам базы данных, которые загружены в кэш статей репликации.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления &#40; связанные с репликацией Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  
