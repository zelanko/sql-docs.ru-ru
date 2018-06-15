---
title: Транзакции | Документы Microsoft
description: Транзакции в драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: fecf4c91b95cdb140261afe5303520d11d63afe7
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308306"
---
# <a name="transactions"></a>Transactions
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server реализует поддержку локальных транзакций. Потребитель может использовать распределенные или координируемые транзакции с помощью координатора распределенных транзакций (Майкрософт) (MS DTC). Для потребителей, которым требуется управление транзакциями, охватывающее несколько сеансов драйвер OLE DB для SQL Server может соединять транзакции, инициированные и обслуживаемые координатором MS DTC.  
  
 По умолчанию драйвер OLE DB для SQL Server использует режим автоматического сохранения транзакций, где каждое отдельное действие в сеансе потребителя составляет полную транзакцию для экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Драйвер OLE DB для SQL Server режим автоматической фиксации локальной и транзакций с автоматической фиксацией никогда не принадлежат более чем одного сеанса.  
  
 Драйвер OLE DB для SQL Server предоставляет **ITransactionLocal** интерфейс, что позволяет потребителю использовать явно и неявно запускаемые транзакции в одном соединении с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Драйвер OLE DB для SQL Server не поддерживает вложенные локальные транзакции.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Поддержка локальных транзакций](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [Поддержка распределенных транзакций](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Уровни изоляции &#40;OLE DB&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>См. также  
 [Программирование драйвера OLE DB для SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
