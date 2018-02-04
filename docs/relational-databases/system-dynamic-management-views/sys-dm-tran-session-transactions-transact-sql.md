---
title: "sys.dm_tran_session_transactions (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/30/2017
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
- dm_tran_session_transactions
- sys.dm_tran_session_transactions
- sys.dm_tran_session_transactions_TSQL
- dm_tran_session_transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_session_transactions dynamic management view
ms.assetid: c7157491-58c2-49fe-87d7-0c9723113adf
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d5c2c3d24b3e3282a2f91038b2989d30679be4f1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmtransessiontransactions-transact-sql"></a>sys.dm_tran_session_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения о взаимосвязях связанных транзакций и сеансов.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_tran_session_transactions**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|session_id|**int**|Идентификатор сеанса, в котором выполняется транзакция.|  
|transaction_id|**bigint**|Идентификатор транзакции.|  
|transaction_descriptor|**binary(8)**|Идентификатор транзакции, который используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для связи с драйвером клиента.|  
|enlist_count|**int**|Количество активных запросов транзакции в сеансе.|  
|is_user_transaction|**бит**|1 = транзакция была инициирована запросом пользователя.<br /><br /> 0 = системная транзакция.|  
|is_local|**бит**|1 = локальная транзакция.<br /><br /> 0 = распределенная транзакция или прикрепленная транзакция связанного сеанса.|  
|is_enlisted|**бит**|1 = является прикрепленной распределенной транзакцией.<br /><br /> 0 = не является прикрепленной распределенной транзакцией.|  
|is_bound|**бит**|1 = транзакция активна в сеансе через связанные сеансы.<br /><br /> 0 = транзакция не активна в сеансе через связанные сеансы.|  
|open_transaction_count||Количество открытых транзакций для каждого сеанса.|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.  
 
 
  
## <a name="remarks"></a>Remarks  
 Через связанные сеансы и распределенные транзакции транзакция может запускаться в нескольких сеансах. В этом случае представление sys.dm_tran_session_transactions покажет несколько строк для одного идентификатора transaction_id — одну для каждого сеанса, в котором выполняется эта транзакция.  
  
 Посредством выполнения множественных запросов в режиме автофиксации с помощью режима MARS, при этом можно иметь несколько транзакций в одном сеансе. В этом случае представление sys.dm_tran_session_transactions покажет несколько строк для одного идентификатора session_id — одну для каждой транзакции, которая выполняется в этом сеансе.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


