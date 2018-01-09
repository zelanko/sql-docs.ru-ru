---
title: "Использование транзакций | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a8beed22985c5f73ff5a4c1fed722fb331155ada
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="using-transactions"></a>Использование транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] управление объектов (SMO), обработка транзакций выполняется через подключение к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> объекта. <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Ссылается объект <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Server> объекта установления соединения. Такие методы, как <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> и <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A>, принадлежат свойству объекта <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений SMO](../../../relational-databases/server-management-objects-smo/create-program/creating-smo-programs.md)  
  
  
