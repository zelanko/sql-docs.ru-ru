---
title: Транзакции | Документы Microsoft
description: Транзакции в драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 31122886213b721eb36a452f651ad4ebd845e941
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="transactions"></a>Transactions
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server реализует поддержку локальных транзакций. Потребитель может использовать распределенные или координируемые транзакции с помощью координатора распределенных транзакций (Майкрософт) (MS DTC). Для потребителей, которым требуется управление транзакциями, охватывающее несколько сеансов драйвер OLE DB для SQL Server может соединять транзакции, инициированные и обслуживаемые координатором MS DTC.  
  
 По умолчанию драйвер OLE DB для SQL Server использует режим автоматического сохранения транзакций, где каждое отдельное действие в сеансе потребителя составляет полную транзакцию для экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Драйвер OLE DB для SQL Server режим автоматической фиксации локальной и транзакций с автоматической фиксацией никогда не принадлежат более чем одного сеанса.  
  
 Драйвер OLE DB для SQL Server предоставляет **ITransactionLocal** интерфейс, что позволяет потребителю использовать явно и неявно запускаемые транзакции в одном соединении с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Драйвер OLE DB для SQL Server не поддерживает вложенные локальные транзакции.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Поддержка локальных транзакций](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [Поддержка распределенных транзакций](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Уровни изоляции &#40;OLE DB&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)  
  
  
