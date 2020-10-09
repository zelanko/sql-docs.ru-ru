---
description: Отсоединение от экземпляра SQL Server
title: Отключение от экземпляра SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2e98180b877fb81c5d32f908a2f8e9cdc131a45a
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91868610"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Отсоединение от экземпляра SQL Server
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Закрытие и отсоединение объектов SMO [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вручную не требуется. Соединения открываются и закрываются по мере необходимости.  
  
## <a name="connection-pooling"></a>Объединение подключений в пул  
 При вызове метода [Connect](/previous-versions/sql/sql-server-2014/ms199449(v=sql.120)) соединение не освобождается автоматически. Метод [Disconnect](/previous-versions/sql/sql-server-2014/ms199428(v=sql.120)) необходимо вызывать явным образом, чтобы освободить подключение к пулу соединений. Можно также запросить соединение вне пула. Это можно сделать, задав свойство [нонпуледконнектион](/previous-versions/sql/sql-server-2014/ms214357(v=sql.120)) <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойства, которое ссылается на объект [ServerConnection](/previous-versions/sql/sql-server-2014/ms218641(v=sql.120)) .  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Отсоединение от экземпляра SQL Server для объектов RMO  
 При программировании с использованием объектов RMO закрытие серверных соединений немного отличается от закрытия при использовании объектов SMO.  
  
 Так как соединение с сервером для объекта RMO поддерживается объектом [ServerConnection](/previous-versions/sql/sql-server-2014/ms218641(v=sql.120)) , этот объект также используется при отключении от экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при программировании с помощью RMO. Чтобы закрыть соединение с помощью объекта [ServerConnection](/previous-versions/sql/sql-server-2014/ms218641(v=sql.120)) , вызовите метод [Disconnect](/previous-versions/sql/sql-server-2014/ms199428(v=sql.120)) объекта RMO. После закрытия соединения объекты RMO использовать нельзя.  
  
## <a name="example"></a>Пример  
Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. [в статье Создание проекта Visual C&#35; SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
 
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Закрытие и отсоединение объекта SMO на языке Visual Basic  
 В этом примере кода показано, как запросить подключение без пула, задав свойство [нонпуледконнектион](/previous-versions/sql/sql-server-2014/ms214357(v=sql.120)) <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойства объекта.  
  
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
 В этом примере кода показано, как запросить подключение без пула, задав свойство [нонпуледконнектион](/previous-versions/sql/sql-server-2014/ms214357(v=sql.120)) <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойства объекта.  
  
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
 [ServerConnection](/previous-versions/sql/sql-server-2014/ms218641(v=sql.120))  
  
