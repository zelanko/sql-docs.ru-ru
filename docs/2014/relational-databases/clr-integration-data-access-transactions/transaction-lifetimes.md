---
title: Время существования транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
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
ms.openlocfilehash: 4a007db3f753bf803e2ecf9b8d1775bd8723ac3b
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37352525"
---
# <a name="transaction-lifetimes"></a>Время существования транзакций
  Между транзакциями, запускаемыми из хранимых процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] и из управляемого кода, имеется существенное различие: код CLR не может разбалансировать состояние транзакции при входе или выходе из вызывающей среды CLR. Необходимо учитывать следующие последствия этого факта.  
  
-   Транзакцию, запущенную в среде CLR, необходимо зафиксировать или выполнить ее откат, иначе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сформирует ошибку при выходе из среды.  
  
-   Внешнюю транзакцию нельзя зафиксировать или выполнить ее откат внутри кода CLR.  
  
-   Попытка зафиксировать транзакцию, запущенную в другой процедуре, вызывает ошибку времени выполнения.  
  
-   Попытка выполнить откат транзакции, запущенной в другой процедуре, приводит к зависанию транзакции (предотвращая выполнение любых других операций с побочными эффектами). Выполнение транзакции прекращается, пока код CLR не выйдет из области действия. Обратите внимание, что эта особенность может быть полезной при обнаружении ошибки в процедуре и необходимости убедиться, что работа транзакции полностью прекращена.  
  
## <a name="see-also"></a>См. также  
 [Интеграция со средой CLR и транзакции](../native-client-ole-db-transactions/transactions.md)  
  
  
