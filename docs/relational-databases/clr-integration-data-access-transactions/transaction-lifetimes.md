---
title: "Время существования транзакций | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 97f594dde59411f05b60d8d778d617955526cad6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="transaction-lifetimes"></a>Время существования транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Имеется существенное различие между транзакциями, запускаемыми [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимых процедур, так и запущен в управляемом коде: среда CLR кода CLR не может разбалансировать состояние транзакции при входе или выходе из вызывающей среды CLR. Необходимо учитывать следующие последствия этого факта.  
  
-   Транзакцию, запущенную в среде CLR, необходимо зафиксировать или выполнить ее откат, иначе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сформирует ошибку при выходе из среды.  
  
-   Внешнюю транзакцию нельзя зафиксировать или выполнить ее откат внутри кода CLR.  
  
-   Попытка зафиксировать транзакцию, запущенную в другой процедуре, вызывает ошибку времени выполнения.  
  
-   Попытка выполнить откат транзакции, запущенной в другой процедуре, приводит к зависанию транзакции (предотвращая выполнение любых других операций с побочными эффектами). Выполнение транзакции прекращается, пока код CLR не выйдет из области действия. Обратите внимание, что эта особенность может быть полезной при обнаружении ошибки в процедуре и необходимости убедиться, что работа транзакции полностью прекращена.  
  
## <a name="see-also"></a>См. также:  
 [Интеграция со средой CLR и транзакции](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
