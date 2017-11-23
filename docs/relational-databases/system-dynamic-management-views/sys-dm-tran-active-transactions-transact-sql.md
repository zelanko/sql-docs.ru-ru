---
title: "sys.dm_tran_active_transactions (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_active_transactions
- sys.dm_tran_active_transactions_TSQL
- dm_tran_active_transactions_TSQL
- dm_tran_active_transactions
dev_langs: TSQL
helpviewer_keywords: sys.dm_tran_active_transactions dynamic management view
ms.assetid: 154ad6ae-5455-4ed2-b014-e443abe2c6ee
caps.latest.revision: "39"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e12a7ff452ed03875a774c665cdc92585950c414
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmtranactivetransactions-transact-sql"></a>sys.dm_tran_active_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает данные о транзакциях для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_tran_active_transactions**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|transaction_id|**bigint**|Идентификатор транзакции на уровне экземпляра, а не на уровне базы данных. Он уникален во всех базах данных только в пределах экземпляра, но не уникален во всех экземплярах сервера.|  
|имя|**nvarchar(32)**|Имя транзакции. Оно перезаписывается, если транзакция помечена, и помеченное имя заменяет имя транзакции.|  
|transaction_begin_time|**datetime**|Время начала транзакции.|  
|transaction_type|**int**|Тип транзакции.<br /><br /> 1 = транзакция чтения-записи<br /><br /> 2 = транзакция только чтения<br /><br /> 3 = системная транзакция<br /><br /> 4 = распределенная транзакция|  
|transaction_uow|**uniqueidentifier**|Идентификатор единицы работы транзакции (UOW) для распределенных транзакций. MS DTC использует идентификатор UOW для работы с распределенной транзакцией.|  
|transaction_state|**int**|0 = Транзакция еще не была полностью инициализирована.<br /><br /> 1 = Транзакция была инициализирована, но еще не началась.<br /><br /> 2 = Транзакция активна.<br /><br /> 3 = Транзакция закончилась. Используется для транзакций «только для чтения».<br /><br /> 4 = Фиксирующий процесс был инициализирован на распределенной транзакции. Предназначено только для распределенных транзакций. Распределенная транзакция все еще активна, но дальнейшая обработка не может иметь место.<br /><br /> 5 = Транзакция находится в готовом состоянии и ожидает разрешения.<br /><br /> 6 = транзакция зафиксирована.<br /><br /> 7 = Производится откат транзакции.<br /><br /> 8 = выполнен откат транзакции.|  
|transaction_status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|transaction_status2|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|dtc_state|**int**|**Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] (первоначального выпуска по [текущего выпуска](http://go.microsoft.com/fwlink/p/?LinkId=299659)).<br /><br /> 1 = ACTIVE<br /><br /> 2 = PREPARED<br /><br /> 3 = COMMITTED<br /><br /> 4 = ABORTED<br /><br /> 5 = RECOVERED|  
|dtc_status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|dtc_isolation_level|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|filestream_transaction_id|**varbinary(128)**|**Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] (первоначального выпуска по [текущего выпуска](http://go.microsoft.com/fwlink/p/?LinkId=299659)).<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Permissions  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.  
 
  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_tran_session_transactions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-session-transactions-transact-sql.md)   
 [sys.dm_tran_database_transactions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-database-transactions-transact-sql.md)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


