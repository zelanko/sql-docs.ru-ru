---
title: Время существования транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 12efdc644c950cecdbd676f53fe582b1d7d20ca6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47774182"
---
# <a name="transaction-lifetimes"></a>Время существования транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Между транзакциями, запускаемыми из хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] и из управляемого кода, имеется существенное различие: код CLR не может разбалансировать состояние транзакции при входе или выходе из вызывающей среды CLR. Необходимо учитывать следующие последствия этого факта.  
  
-   Транзакцию, запущенную в среде CLR, необходимо зафиксировать или выполнить ее откат, иначе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сформирует ошибку при выходе из среды.  
  
-   Внешнюю транзакцию нельзя зафиксировать или выполнить ее откат внутри кода CLR.  
  
-   Попытка зафиксировать транзакцию, запущенную в другой процедуре, вызывает ошибку времени выполнения.  
  
-   Попытка выполнить откат транзакции, запущенной в другой процедуре, приводит к зависанию транзакции (предотвращая выполнение любых других операций с побочными эффектами). Выполнение транзакции прекращается, пока код CLR не выйдет из области действия. Обратите внимание, что эта особенность может быть полезной при обнаружении ошибки в процедуре и необходимости убедиться, что работа транзакции полностью прекращена.  
  
## <a name="see-also"></a>См. также  
 [Интеграция со средой CLR и транзакции](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
