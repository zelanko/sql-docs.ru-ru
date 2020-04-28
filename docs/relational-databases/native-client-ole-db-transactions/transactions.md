---
title: Транзакции | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8779b68d6ab1070514f8ef6685ef378437d09539
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302545"
---
# <a name="transactions"></a>Транзакции
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента реализует поддержку локальных транзакций. Потребитель может использовать распределенные или координируемые транзакции с помощью координатора распределенных транзакций (Майкрософт) (MS DTC). Для потребителей, которым необходим контроль транзакций, охватывающий несколько сеансов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , поставщик OLE DB собственного клиента может присоединить транзакции, инициированные и ОБСЛУЖИВАЕМЫЕ MS DTC.  
  
 По умолчанию поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента использует режим автоматической фиксации транзакций, где каждое дискретное действие в сеансе потребителя состоит из полной транзакции с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Режим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматической фиксации поставщика собственного клиента OLE DB является локальным, и транзакции с автоматической фиксацией никогда не охватывают более одного сеанса.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента предоставляет интерфейс **ITransactionLocal** , позволяя потребителю явно и неявно запускать транзакции в одном соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB не поддерживает вложенные локальные транзакции.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Поддержка локальных транзакций](../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md)  
  
-   [Поддержка распределенных транзакций](../../relational-databases/native-client-ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Уровни изоляции (OLE DB)](../../relational-databases/native-client-ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (OLE DB)](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
