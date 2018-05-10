---
title: sys.dm_tran_session_transactions (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4df6afdab47fc0da07412223b394ad0dc77a81f7
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
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
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="remarks"></a>Замечания  
 Через связанные сеансы и распределенные транзакции транзакция может запускаться в нескольких сеансах. В этом случае представление sys.dm_tran_session_transactions покажет несколько строк для одного идентификатора transaction_id — одну для каждого сеанса, в котором выполняется эта транзакция.  
  
 Посредством выполнения множественных запросов в режиме автофиксации с помощью режима MARS, при этом можно иметь несколько транзакций в одном сеансе. В этом случае представление sys.dm_tran_session_transactions покажет несколько строк для одного идентификатора session_id — одну для каждой транзакции, которая выполняется в этом сеансе.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


