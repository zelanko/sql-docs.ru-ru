---
title: Реализация конечных точек | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- endpoints [SMO]
ms.assetid: f8674dbb-9bc0-488f-9def-e9e0ce1ddf86
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 17e154743d221cfd4a2070c56634c6364a910afb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48081643"
---
# <a name="implementing-endpoints"></a>Реализация конечных точек
  Конечная точка представляет собой службу, в функции которой входит прослушивание запросов. SMO поддерживаются разные типы конечных точек с помощью <xref:Microsoft.SqlServer.Management.Smo.Endpoint> объекта. Для обработки конкретного типа полезных данных можно создать службу конечной точки, которая будет использовать указанный протокол, создав экземпляр объекта <xref:Microsoft.SqlServer.Management.Smo.Endpoint> и настроив его свойства.  
  
 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A> Свойство <xref:Microsoft.SqlServer.Management.Smo.Endpoint> объект может использоваться для указания следующих типов полезных данных:  
  
-   Зеркальное отображение базы данных  
  
-   SOAP (поддержка для конечных точек SOAP предусмотрена в версии [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] и в предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)])  
  
-   Компонент Service Broker  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)]  
  
 Кроме того, свойство <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> может использоваться для указания следующих двух поддерживаемых протоколов:  
  
-   протокол HTTP;  
  
-   протокол TCP.  
  
 Указан тип полезных данных, фактически применяемые полезные данные можно установить с помощью <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A> свойство объекта. Свойство объекта <xref:Microsoft.SqlServer.Management.Smo.Payload> обеспечивает ссылку на объект полезных данных указанного типа, свойства которого можно изменить.  
  
 Для объекта <xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload> необходимо указать роль для зеркального отображения и отметить, включать ли шифрование. <xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload> Объекта требуются сведения о перенаправлении сообщений, максимальное число разрешенных подключений и режим проверки подлинности. Для объекта <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> надо указать множество устанавливаемых свойств, включая свойство <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> объекта, которое указывает доступные клиентам методы полезных данных SOAP (хранимые процедуры и определяемые пользователем функции).  
  
 Аналогично этому фактически применяемый протокол можно установить с помощью свойства <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> объекта, которое ссылается на объект протокола типа, указанного в свойстве <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A>. Объекту <xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> требуется список ограниченных IP-адресов, а также сведения о порте, веб-сайте и проверке подлинности. <xref:Microsoft.SqlServer.Management.Smo.TcpProtocol> Объекта также необходим список ограниченных IP-адресов и сведения о порте.  
  
 После того как конечная точка будет создана и полностью определена, можно предоставлять, отменять и запрещать доступ к ней пользователям базы данных, группам, ролям и именам входа.  
  
## <a name="example"></a>Пример  
 В следующем примере кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в разделе [Создание проекта SMO на Visual Basic в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) и [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-basic"></a>Создание конечной точки зеркального отображения базы данных на языке Visual Basic  
 Этот пример кода показывает, как создать конечную точку зеркального отображения базы данных в SMO. Это надо сделать до того, как будет формироваться зеркальное отображение базы данных. Воспользуйтесь свойством <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> и другими свойствами объекта <xref:Microsoft.SqlServer.Management.Smo.Database> для создания зеркального отображения базы данных.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEndpoints1](SMO How to#SMO_VBEndpoints1)]  -->  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-c"></a>Создание конечной точки зеркального отображения базы данных на языке Visual C#  
 Этот пример кода показывает, как создать конечную точку зеркального отображения базы данных в SMO. Это надо сделать до того, как будет формироваться зеркальное отображение базы данных. Воспользуйтесь свойством <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> и другими свойствами объекта <xref:Microsoft.SqlServer.Management.Smo.Database> для создания зеркального отображения базы данных.  
  
```  
{  
            //Set up a database mirroring endpoint on the server before   
        //setting up a database mirror.   
        //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Define an Endpoint object variable for database mirroring.   
            Endpoint ep = default(Endpoint);  
            ep = new Endpoint(srv, "Mirroring_Endpoint");  
            ep.ProtocolType = ProtocolType.Tcp;  
            ep.EndpointType = EndpointType.DatabaseMirroring;  
            //Specify the protocol ports.   
            ep.Protocol.Http.SslPort = 5024;  
            ep.Protocol.Tcp.ListenerPort = 6666;  
            //Specify the role of the payload.   
            ep.Payload.DatabaseMirroring.ServerMirroringRole = ServerMirroringRole.All;  
            //Create the endpoint on the instance of SQL Server.   
            ep.Create();  
            //Start the endpoint.   
            ep.Start();  
            Console.WriteLine(ep.EndpointState);  
        }  
```  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-powershell"></a>Создание конечной точки зеркального отображения базы данных в PowerShell  
 Этот пример кода показывает, как создать конечную точку зеркального отображения базы данных в SMO. Это надо сделать до того, как будет формироваться зеркальное отображение базы данных. Воспользуйтесь свойством <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> и другими свойствами объекта <xref:Microsoft.SqlServer.Management.Smo.Database> для создания зеркального отображения базы данных.  
  
```  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Get a new endpoint to congure and add  
$ep = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Endpoint -argumentlist $srv,"Mirroring_Endpoint"  
  
#Set some properties  
$ep.ProtocolType = [Microsoft.SqlServer.Management.SMO.ProtocolType]::Tcp  
$ep.EndpointType = [Microsoft.SqlServer.Management.SMO.EndpointType]::DatabaseMirroring  
$ep.Protocol.Http.SslPort = 5024  
$ep.Protocol.Tcp.ListenerPort = 6666 #inline comment  
$ep.Payload.DatabaseMirroring.ServerMirroringRole = [Microsoft.SqlServer.Management.SMO.ServerMirroringRole]::All  
  
# Create the endpoint on the instance  
$ep.Create()  
  
# Start the endpoint  
$ep.Start()  
  
# Report its state  
$ep.EndpointState;  
```  
  
## <a name="see-also"></a>См. также  
 [Конечная точка зеркального отображения базы данных (SQL Server)](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
