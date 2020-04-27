---
title: Уровни изоляции (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: a18986af71f652a833f413ee1fa62ca2fd44ba06
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63215995"
---
# <a name="isolation-levels-ole-db"></a>Уровни изоляции (OLE DB)
  Клиенты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут управлять уровнями изоляции транзакций для соединения. Чтобы управлять уровнем изоляции транзакций, потребитель поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента использует:  
  
-   DBPROPSET_SESSION DBPROP_SESS_AUTOCOMMITISOLEVELS свойства для режима [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматической фиксации по умолчанию для поставщика собственного клиента OLE DB.  
  
     Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента для уровня по умолчанию имеет значение DBPROPVAL_TI_READCOMMITTED.  
  
-   Параметр *isoLevel* метода **ITransactionLocal::StartTransaction** для локальных транзакций с ручной фиксацией.  
  
-   Параметр *isoLevel* метода **ITransactionDispenser::BeginTransaction** для распределенных транзакций с координацией MS DTC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешает доступ только для чтения на уровне изоляции чтения «грязных» данных. Все другие уровни ограничивают параллелизм применением блокировок к объектам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если клиент требует более высоких уровней параллелизма, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] применяет более строгие ограничения на параллельные обращения к данным. Чтобы обеспечить максимальный уровень одновременного доступа к данным, потребитель поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB собственного клиента должен управлять своими запросами для конкретных уровней параллелизма.  
  
> [!NOTE]  
>  В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] появился уровень изоляции моментального снимка. Дополнительные сведения см. в разделе [Working with Snapshot Isolation](../native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>См. также  
 [Транзакции](transactions.md)  
  
  
