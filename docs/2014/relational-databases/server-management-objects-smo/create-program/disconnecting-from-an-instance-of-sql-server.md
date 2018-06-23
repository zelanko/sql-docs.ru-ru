---
title: Отсоединение от экземпляра SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f2ce4ae7ce42df42be9b6bc68c3d13acf949dba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189205"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Отсоединение от экземпляра SQL Server
  Вручную закрытие и отсоединение [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] управляющих объектов (SMO) не требуется. Соединения открываются и закрываются по мере необходимости.  
  
## <a name="connection-pooling"></a>Организация пулов соединений  
 Когда <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> вызывается метод, соединение не освобождается автоматически. Чтобы освободить соединение обратно в пул, необходимо явно вызвать метод <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A>. Можно также запросить соединение вне пула. Это делается путем установки свойства <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> свойства <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>, которое ссылается на объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Отсоединение от экземпляра SQL Server для объектов RMO  
 При программировании с использованием объектов RMO закрытие серверных соединений немного отличается от закрытия при использовании объектов SMO.  
  
 Так как соединение с сервером для объекта RMO обслуживается <xref:Microsoft.SqlServer.Management.Common.ServerConnection> объекта, этот объект также используется при отсоединении от экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при программировании с помощью объектов RMO. Закрыть подключение с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , вызовите <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> метод объекта RMO. После закрытия соединения объекты RMO использовать нельзя.  
  
## <a name="example"></a>Пример  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Закрытие и отсоединение объекта SMO на языке Visual Basic  
 Данный пример кода показывает, как запросить соединение вне пула, задав <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойство объекта.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB4](SMO How to#SMO_VB4)]  -->  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Закрытие и отсоединение объекта SMO на языке Visual C#  
 Данный пример кода показывает, как запросить соединение вне пула, задав <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойство объекта.  
  
```  
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
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  