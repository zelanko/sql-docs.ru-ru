---
title: Транзакции | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dca9b7a3289390b1d1e20e1b0d18c23b44b87617
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145501"
---
# <a name="transactions"></a>Transactions
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента реализует поддержку локальных транзакций. Потребитель может использовать распределенные или координируемые транзакции с помощью координатора распределенных транзакций (Майкрософт) (MS DTC). Для потребителей, которым требуется управление транзакциями, охватывающее несколько сеансов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента может соединять транзакции, инициированные и обслуживаемые координатором MS DTC.  
  
 По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента использует режим автоматической фиксации транзакции, где каждое отдельное действие в сеансе потребителя составляет полную транзакцию для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Локальный режим автоматической фиксации поставщика OLE DB для собственного клиента, и транзакции с автоматической фиксацией никогда не принадлежат более чем за один сеанс.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента предоставляет **ITransactionLocal** интерфейс, что позволяет потребителю использовать явно и неявно запускаемые транзакции в одном соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента не поддерживает вложенные локальные транзакции.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Поддержка локальных транзакций](supporting-local-transactions.md)  
  
-   [Поддержка распределенных транзакций](supporting-distributed-transactions.md)  
  
-   [Уровни изоляции &#40;OLE DB&#41;](isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
