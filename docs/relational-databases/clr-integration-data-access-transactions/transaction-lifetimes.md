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
ms.openlocfilehash: 759af22d445bb3c67db1f39ecf69dbeee1b666fe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67902479"
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
  
  
