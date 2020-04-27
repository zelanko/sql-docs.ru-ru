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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63213895"
---
# <a name="transactions"></a>Transactions
  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента реализует поддержку локальных транзакций. Потребитель может использовать распределенные или координируемые транзакции с помощью координатора распределенных транзакций (Майкрософт) (MS DTC). Для потребителей, которым необходим контроль транзакций, охватывающий несколько сеансов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , поставщик OLE DB собственного клиента может присоединить транзакции, инициированные и ОБСЛУЖИВАЕМЫЕ MS DTC.  
  
 По умолчанию поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента использует режим автоматической фиксации транзакций, где каждое дискретное действие в сеансе потребителя состоит из полной транзакции с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Режим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматической фиксации поставщика собственного клиента OLE DB является локальным, и транзакции с автоматической фиксацией никогда не охватывают более одного сеанса.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента предоставляет интерфейс **ITransactionLocal** , позволяя потребителю явно и неявно запускать транзакции в одном соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB не поддерживает вложенные локальные транзакции.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Поддержка локальных транзакций](supporting-local-transactions.md)  
  
-   [Поддержка распределенных транзакций](supporting-distributed-transactions.md)  
  
-   [Уровни изоляции (OLE DB)](isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (OLE DB)](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
