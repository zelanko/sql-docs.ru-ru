---
title: CURRENT_TRANSACTION_ID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CURRENT_TRANSACTION_ID
- CURRENT_TRANSACTION_ID_TSQL
- sys.CURRENT_TRANSACTION_ID
- sys.CURRENT_TRANSACTION_ID_TSQL
helpviewer_keywords:
- CURRENT_TRANSACTION_ID function
ms.assetid: 82cd9f92-d935-45a0-a433-620d6e15b467
caps.latest.revision: 6
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b5170c6a3b96710ea42d1acdb88256c33be0eb6d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="currenttransactionid-transact-sql"></a>CURRENT_TRANSACTION_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Возвращает идентификатор текущей транзакции в текущем сеансе.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CURRENT_TRANSACTION_ID( )  
  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных
**bigint**
  
## <a name="return-value"></a>Возвращаемое значение  
Идентификатор текущей транзакции в текущем сеансе, полученный из представления [sys.dm_tran_current_transaction (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-tran-current-transaction-transact-sql.md).
  
## <a name="permissions"></a>Разрешения  
Любой пользователь может вернуть идентификатор транзакции текущего сеанса.
  
## <a name="examples"></a>Примеры  
В приведенном ниже примере возвращается идентификатор транзакции текущего сеанса.
  
```sql
SELECT CURRENT_TRANSACTION_ID();  
```  
  
## <a name="see-also"></a>См. также раздел
[sp_set_session_context (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md)  
[SESSION_CONTEXT (Transact-SQL)](../../t-sql/functions/session-context-transact-sql.md)  
[Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)  
[CONTEXT_INFO (Transact-SQL)](../../t-sql/functions/context-info-transact-sql.md)  
[SET CONTEXT_INFO (Transact-SQL)](../../t-sql/statements/set-context-info-transact-sql.md)
  
  
