---
title: "Транзакции (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Transactions
- Transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transactions [SQL Server]
- transactions [SQL Server], about transactions
- UOW [SQL Server]
- unit of work [SQL Server]
ms.assetid: 1485c375-921a-42af-a871-bb333cc08d3e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 360d2d4d88280a011687dfb3845f1de86513bdc8
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="transactions-transact-sql"></a>Транзакции (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Транзакция является единственной единицей работы. Если транзакция выполнена успешно, все модификации данных, сделанные в течение транзакции, принимаются и становятся постоянной частью базы данных. Если в результате выполнения транзакции происходят ошибки и должна быть произведена отмена или выполнен откат, все модификации данных будут отменены.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]работает в следующих режимах транзакций.  
  
 Автоматическое принятие транзакций  
 Каждая отдельная инструкция является транзакцией.  
  
 Явные транзакции  
 Каждая транзакция явно начинается с инструкции BEGIN TRANSACTION и явно заканчивается инструкцией COMMIT или ROLLBACK.  
  
 Неявные транзакции  
 Новая транзакция неявно начинается, когда предыдущая транзакция завершена, но каждая транзакция явно завершается инструкцией COMMIT или ROLLBACK.  
  
 Транзакции контекста пакета  
 Будучи применимой только к множественным активным результирующим наборам (режим MARS), явная или неявная транзакция [!INCLUDE[tsql](../../includes/tsql-md.md)], которая запускается в сеансе режима MARS, становится транзакцией контекста пакета. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически выполняет откат транзакции контекста пакета, если эта транзакция не зафиксирована или выполнен ее откат при завершении пакета.  

> [!NOTE] 
> Особые замечания, относящиеся к продуктам хранилища данных, в разделе [транзакции (хранилище данных SQL)](transactions-sql-data-warehouse.md).   

## <a name="in-this-section"></a>В этом разделе  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]предоставляет следующие инструкции транзакций:  
  
|||  
|-|-|  
|[BEGIN DISTRIBUTED TRANSACTION](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)|[ROLLBACK TRANSACTION](../../t-sql/language-elements/rollback-transaction-transact-sql.md)|  
|[BEGIN TRANSACTION](../../t-sql/language-elements/begin-transaction-transact-sql.md)|[ROLLBACK WORK](../../t-sql/language-elements/rollback-work-transact-sql.md)|  
|[COMMIT TRANSACTION](../../t-sql/language-elements/commit-transaction-transact-sql.md)|[SAVE TRANSACTION](../../t-sql/language-elements/save-transaction-transact-sql.md)|  
|[COMMIT WORK](../../t-sql/language-elements/commit-work-transact-sql.md)||  
  
## <a name="see-also"></a>См. также  
 [SET IMPLICIT_TRANSACTIONS &#40; Transact-SQL &#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
