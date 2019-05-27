---
title: ROLLBACK WORK (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ROLLBACK WORK
- ROLLBACK_WORK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transaction rollbacks [SQL Server]
- erasing data modifications [SQL Server]
- ROLLBACK WORK statement
- roll back transactions [SQL Server]
- rolling back transactions, ROLLBACK WORK
- savepoints [SQL Server]
ms.assetid: 2071dbd3-53d5-4510-be8d-26e80f2553b4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 10a10b92a18566ca7a9ffaa8d5a4a80d69f3420b
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65980308"
---
# <a name="rollback-work-transact-sql"></a>ROLLBACK WORK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Выполняет откат пользовательской транзакции на начало транзакции.  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ROLLBACK [ WORK ]  
[ ; ]  
```  
  
## <a name="remarks"></a>Remarks  
 Эта инструкция действует так же, как и инструкция ROLLBACK TRANSACTION, с тем лишь отличием, что ROLLBACK TRANSACTION допускает применение определяемых пользователем имен транзакций. Вне зависимости от того, используется ли дополнительное ключевое слово WORK, синтаксис ROLLBACK совместим со стандартом ISO.  
  
 При вложении транзакций инструкция ROLLBACK WORK всегда откатывается до самой удаленной инструкции BEGIN TRANSACTION и уменьшает на единицу системную функцию @@TRANCOUNT до достижения последней значения 0.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию инструкцию ROLLBACK WORK разрешено выполнять любым пользователям.  
  
## <a name="see-also"></a>См. также:  
 [BEGIN DISTRIBUTED TRANSACTION (Transact-SQL)](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [BEGIN TRANSACTION (Transact-SQL)](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT TRANSACTION (Transact-SQL)](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [COMMIT WORK (Transact-SQL)](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION (Transact-SQL)](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [SAVE TRANSACTION (Transact-SQL)](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  
