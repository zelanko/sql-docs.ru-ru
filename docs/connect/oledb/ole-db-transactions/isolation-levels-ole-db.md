---
title: Уровни изоляции (OLE DB) | Документы Microsoft
description: Уровни изоляции (OLE DB)
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
- isolation levels [OLE DB]
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 0774a7743cc9993b05f1470be31faf482147d282
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306773"
---
# <a name="isolation-levels-ole-db"></a>Уровни изоляции (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Клиенты [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] могут управлять уровнями изоляции транзакций для соединения. Чтобы управлять уровнем изоляции транзакций, использует драйвер OLE DB для объекта-получателя SQL Server:  
  
-   Свойство DBPROP_SESS_AUTOCOMMITISOLEVELS драйвера OLE DB для SQL Server режим автоматической фиксации по умолчанию.  
  
     Драйвер OLE DB для SQL Server по умолчанию для уровня — DBPROPVAL_TI_READCOMMITTED.  
  
-   *IsoLevel* параметр **ITransactionLocal::StartTransaction** метод для локальных ручной фиксации транзакций.  
  
-   *IsoLevel* параметр **ITransactionDispenser::BeginTransaction** метод координацией MS DTC распределенные транзакции.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] разрешает доступ только для чтения на уровне изоляции чтения «грязных» данных. Все другие уровни ограничивают параллелизм применением блокировок к объектам [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если клиент требует более высоких уровней параллелизма, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] применяет более строгие ограничения на параллельные обращения к данным. Чтобы обеспечить высокий уровень параллельного доступа к данным, драйвер OLE DB для SQL Server потребитель должен интеллектуально управлять запросами для конкретных уровней параллелизма.  
  
> [!NOTE]  
>  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] появился уровень изоляции моментального снимка. Дополнительные сведения см. в разделе [работа с изоляцией моментального снимка](../../oledb/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>См. также  
 [Transactions](../../oledb/ole-db-transactions/transactions.md)  
  
  
