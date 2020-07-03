---
title: Использование транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3d78bcc4e4b561583c52fdf6542c26f007c56d48
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901707"
---
# <a name="using-transactions"></a>Использование транзакций
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw.md)]

  В управляющих объектах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SMO) обработка транзакций выполняется через соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. <xref:Microsoft.SqlServer.Management.Common.ServerConnection>На объект ссылается <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Server> объекта при установлении соединения. Такие методы, как <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> и <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A>, принадлежат свойству объекта <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>.  
  
## <a name="see-also"></a>См. также  
 [Создание приложений SMO](../../../relational-databases/server-management-objects-smo/create-program/creating-smo-programs.md)  
  
  
