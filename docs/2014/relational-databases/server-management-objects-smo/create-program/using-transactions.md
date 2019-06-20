---
title: Использование транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 83baa905887609e89b372d4820346ab9aa97a056
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63192014"
---
# <a name="using-transactions"></a>Использование транзакций
  В управляющих объектах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SMO) обработка транзакций выполняется через соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Объект ссылается <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Server> объекта при установлении соединения. Такие методы, как <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> и <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A>, принадлежат свойству объекта <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>.  
  
## <a name="see-also"></a>См. также  
 [Создание приложений SMO](creating-smo-programs.md)  
  
  
