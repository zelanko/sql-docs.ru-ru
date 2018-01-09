---
title: "Отсоединение от экземпляра SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 08/06/2017
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
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
caps.latest.revision: "45"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ad257fc7f6c68ff08beaa223d57e3c83519644c9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Отсоединение от экземпляра SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Вручную закрытие и отсоединение [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] управляющих объектов (SMO) не требуется. Соединения открываются и закрываются по мере необходимости.  
  
## <a name="connection-pooling"></a>Организация пулов соединений  
 Когда [Connect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.connect) вызывается метод, соединение не освобождается автоматически. [Disconnect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) метод должен вызываться явным образом для освобождения соединения в пул подключений. Можно также запросить соединение вне пула. Это можно сделать, задав [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) свойство <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойство, которое ссылается [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) объекта.  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Отсоединение от экземпляра SQL Server для объектов RMO  
 При программировании с использованием объектов RMO закрытие серверных соединений немного отличается от закрытия при использовании объектов SMO.  
  
 Так как соединение с сервером для объекта RMO обслуживается [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) объекта, этот объект также используется при отсоединении от экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при программировании с помощью объектов RMO. Закрыть подключение с помощью [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) , вызовите [Disconnect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) метод объекта RMO. После закрытия соединения объекты RMO использовать нельзя.  
  
## <a name="example"></a>Пример  
Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Create Visual C# 35; Проект SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
 
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Закрытие и отсоединение объекта SMO на языке Visual Basic  
 Данный пример кода показывает, как запросить соединение вне пула, задав [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) свойство <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойство объекта.  
  
```VBNET
Dim srv As Server
srv = New Server
'Disable automatic disconnection.
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect
'Connect to the local, default instance of SQL Server.
srv.ConnectionContext.Connect()
'The actual connection is made when a property is retrieved.
Console.WriteLine(srv.Information.Version)
'Disconnect explicitly.
srv.ConnectionContext.Disconnect()
```
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Закрытие и отсоединение объекта SMO на языке Visual C#  
 Данный пример кода показывает, как запросить соединение вне пула, задав [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) свойство <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойство объекта.  
  
```csharp  
{   
Server srv;   
srv = new Server();   
//Disable automatic disconnection.   
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect;   
//Connect to the local, default instance of SQL Server.   
srv.ConnectionContext.Connect();   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
//Disconnect explicitly.   
srv.ConnectionContext.Disconnect();  
}  
```  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)  
  
  
