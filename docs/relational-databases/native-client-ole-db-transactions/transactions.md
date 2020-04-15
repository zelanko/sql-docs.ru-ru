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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302545"
---
# <a name="transactions"></a>Transactions
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB осуществляет локальную поддержку транзакций. Потребитель может использовать распределенные или координируемые транзакции с помощью координатора распределенных транзакций (Майкрософт) (MS DTC). Для потребителей, требующих контроля транзакций, который охватывает несколько сеансов, поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB может присоединиться к транзакциям, инициированным и поддерживаемым MS DTC.  
  
 По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB использует режим транзакции autocommit, в котором каждое дискретное действие на сеансе потребителя включает в себя полную транзакцию против экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Режим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматического коммипенмента поставщика Native Client OLE DB является локальным, и транзакции автофиксации не охватывают более одного сеанса.  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB предоставляет интерфейс **ITransactionLocal,** позволяя потребителю использовать явно и косвенно начать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]транзакции по одному подключению к экземпляру . Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB не поддерживает вложенные локальные транзакции.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Поддержка локальных транзакций](../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md)  
  
-   [Поддержка распределенных транзакций](../../relational-databases/native-client-ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Уровни изоляции (OLE DB)](../../relational-databases/native-client-ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (OLE DB)](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
