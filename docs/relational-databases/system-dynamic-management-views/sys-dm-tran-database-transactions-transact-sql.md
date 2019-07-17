---
title: sys.dm_tran_database_transactions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_tran_database_transactions
- sys.dm_tran_database_transactions_TSQL
- dm_tran_database_transactions_TSQL
- sys.dm_tran_database_transactions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_database_transactions dynamic management view
ms.assetid: 82a44295-4cbc-4a5b-891a-8ebaf307b8f5
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fd33a84393fb88e0a2a8cdf4d04df6da9883ba28
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262642"
---
# <a name="sysdmtrandatabasetransactions-transact-sql"></a>sys.dm_tran_database_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения о транзакциях на уровне базы данных.  
  
> [!NOTE]  
>  Для вызова этого динамического административного Представления из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_tran_database_transactions**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|transaction_id|**bigint**|Идентификатор транзакции на уровне экземпляра, а не на уровне базы данных. Уникален в пределах баз данных экземпляра, но не уникален в пределах экземпляров сервера.|  
|database_id|**int**|Идентификатор базы данных, связанной с транзакцией.|  
|database_transaction_begin_time|**datetime**|Момент времени, с которого база данных задействована в транзакции. Точнее, это время первой записи журнала в базе данных для данной транзакции.|  
|database_transaction_type|**int**|1 = транзакция чтения-записи<br /><br /> 2 = транзакция только чтения<br /><br /> 3 = системная транзакция|  
|database_transaction_state|**int**|1 = Транзакция не инициализирована.<br /><br /> 3 = Транзакция инициализирована, но в ней еще не сформировано ни одной записи журнала.<br /><br /> 4 = В транзакции имеются сформированные записи журнала.<br /><br /> 5 = Транзакция подготовлена.<br /><br /> 10 = Транзакция зафиксирована.<br /><br /> 11 = Транзакция находится в процессе отката.<br /><br /> 12 = Транзакция находится в стадии фиксации. (Запись журнала формируется, но не материализованного или не сохраняются.)|  
|database_transaction_status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|database_transaction_status2|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|database_transaction_log_record_count|**bigint**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Число записей журнала, сформированных в базе данных для этой транзакции.|  
|database_transaction_replicate_record_count|**int**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Число записей журнала, созданных в базе данных для транзакции, которая реплицируется.|  
|database_transaction_log_bytes_used|**bigint**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Число байтов, используемых журналом базы данных для данной транзакции.|  
|database_transaction_log_bytes_reserved|**bigint**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Число байтов, зарезервированных в журнале базы данных для данной транзакции.|  
|database_transaction_log_bytes_used_system|**int**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Число байтов, занятых в журнале базы данных для системных транзакций от имени данной транзакции.|  
|database_transaction_log_bytes_reserved_system|**int**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Число байтов, зарезервированных в журнале базы данных для системных транзакций от имени данной транзакции.|  
|database_transaction_begin_lsn|**numeric(25,0)**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Регистрационный номер транзакции в журнале (номер LSN) начальной записи для данной транзакции в журнале базы данных.|  
|database_transaction_last_lsn|**numeric(25,0)**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Номер LSN последней сохраненной записи для данной транзакции в журнале базы данных.|  
|database_transaction_most_recent_savepoint_lsn|**numeric(25,0)**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Номер LSN самой последней точки сохранения для данной транзакции в журнале базы данных.|  
|database_transaction_commit_lsn|**numeric(25,0)**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Номер LSN записи фиксации для данной транзакции в журнале базы данных.|  
|database_transaction_last_rollback_lsn|**numeric(25,0)**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Номер LSN транзакции в журнале, до которой произошел последний откат. Если откат не было выполнено, значение будет равно MaxLSN.|  
|database_transaction_next_undo_lsn|**numeric(25,0)**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Номер LSN следующей записи для отката.|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратора сервера** или **администратор Azure Active Directory** учетной записи.   

## <a name="see-also"></a>См. также  
 [sys.dm_tran_active_transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-transactions-transact-sql.md)   
 [sys.dm_tran_session_transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-session-transactions-transact-sql.md)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


