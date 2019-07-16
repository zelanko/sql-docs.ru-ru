---
title: Уровни изоляции (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d17649720fe92f23b0b7aa4fcc8a90657c202ec0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069496"
---
# <a name="isolation-levels-ole-db"></a>Уровни изоляции (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Клиенты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут управлять уровнями изоляции транзакций для соединения. Чтобы управлять уровнем изоляции транзакций, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребитель вызывает поставщик OLE DB для собственного клиента:  
  
-   Свойство DBPROP_SESS_AUTOCOMMITISOLEVELS параметра DBPROPSET_SESSION для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] режим автоматической фиксации по умолчанию поставщик OLE DB для собственного клиента.  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] По умолчанию поставщик OLE DB для собственного клиента для уровня — DBPROPVAL_TI_READCOMMITTED.  
  
-   Параметр *isoLevel* метода **ITransactionLocal::StartTransaction** для локальных транзакций с ручной фиксацией.  
  
-   Параметр *isoLevel* метода **ITransactionDispenser::BeginTransaction** для распределенных транзакций с координацией MS DTC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешает доступ только для чтения на уровне изоляции чтения «грязных» данных. Все другие уровни ограничивают параллелизм применением блокировок к объектам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если клиент требует более высоких уровней параллелизма, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] применяет более строгие ограничения на параллельные обращения к данным. Для поддержания высочайшего уровня параллельного доступа к данным, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителем поставщика OLE DB для собственного клиента должен интеллектуально управлять запросами для конкретных уровней параллелизма.  
  
> [!NOTE]  
>  В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] появился уровень изоляции моментального снимка. Дополнительные сведения см. в разделе [Working with Snapshot Isolation](../../relational-databases/native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>См. также  
 [Transactions](../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
