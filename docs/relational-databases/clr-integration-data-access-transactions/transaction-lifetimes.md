---
title: Время существования транзакций | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
caps.latest.revision: 10
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2c78887d28fdc202da63f58167b4fb414e905f58
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="transaction-lifetimes"></a>Время существования транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Между транзакциями, запускаемыми из хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] и из управляемого кода, имеется существенное различие: код CLR не может разбалансировать состояние транзакции при входе или выходе из вызывающей среды CLR. Необходимо учитывать следующие последствия этого факта.  
  
-   Транзакцию, запущенную в среде CLR, необходимо зафиксировать или выполнить ее откат, иначе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сформирует ошибку при выходе из среды.  
  
-   Внешнюю транзакцию нельзя зафиксировать или выполнить ее откат внутри кода CLR.  
  
-   Попытка зафиксировать транзакцию, запущенную в другой процедуре, вызывает ошибку времени выполнения.  
  
-   Попытка выполнить откат транзакции, запущенной в другой процедуре, приводит к зависанию транзакции (предотвращая выполнение любых других операций с побочными эффектами). Выполнение транзакции прекращается, пока код CLR не выйдет из области действия. Обратите внимание, что эта особенность может быть полезной при обнаружении ошибки в процедуре и необходимости убедиться, что работа транзакции полностью прекращена.  
  
## <a name="see-also"></a>См. также:  
 [Интеграция со средой CLR и транзакции](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
