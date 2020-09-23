---
title: Уровни изоляции (драйвер OLE DB) | Документация Майкрософт
description: Узнайте, как объект-получатель OLE DB Driver for SQL Server может управлять уровнем изоляции транзакций для соединения.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 87b3a348a7219eda5868223b167b2ecf851c2079
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861884"
---
# <a name="isolation-levels-ole-db"></a>Уровни изоляции (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Клиенты [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] могут управлять уровнями изоляции транзакций для соединения. Для управления уровнем изоляции транзакций пользователю OLE DB Driver for SQL Server предоставлены следующие возможности.  
  
-   Свойство DBPROP_SESS_AUTOCOMMITISOLEVELS объекта DBPROPSET_SESSION для используемого по умолчанию режима автоматической фиксации драйвера OLE DB для SQL Server.  
  
     По умолчанию для уровня изоляции в OLE DB Driver for SQL Server устанавливается значение DBPROPVAL_TI_READCOMMITTED.  
  
-   Параметр *isoLevel* метода **ITransactionLocal::StartTransaction** для локальных транзакций с ручной фиксацией.  
  
-   Параметр *isoLevel* метода **ITransactionDispenser::BeginTransaction** для распределенных транзакций с координацией MS DTC.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] разрешает доступ только для чтения на уровне изоляции чтения «грязных» данных. Все другие уровни ограничивают параллелизм применением блокировок к объектам [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если клиент требует более высоких уровней параллелизма, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] применяет более строгие ограничения на параллельные обращения к данным. Чтобы обеспечить самый высокий уровень параллельного доступа к данным, драйвер OLE DB для SQL Server должен интеллектуально управлять запросами для конкретных уровней параллелизма.  
  
> [!NOTE]  
>  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] появился уровень изоляции моментального снимка. Дополнительные сведения см. в разделе [Working with Snapshot Isolation](../../oledb/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>См. также:  
 [Транзакции](../../oledb/ole-db-transactions/transactions.md)  
  
  
