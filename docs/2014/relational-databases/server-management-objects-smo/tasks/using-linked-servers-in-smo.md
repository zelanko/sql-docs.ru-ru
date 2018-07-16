---
title: Использование связанных серверов в объектах SMO | Документация Майкрософт
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
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 57c84f885a53fd2b277fbb34c9bfecc178e0fe89
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319924"
---
# <a name="using-linked-servers-in-smo"></a>Использование связанных серверов в объектах SMO
  Связанный сервер представляет источник данных OLE DB на удаленном сервере. Удаленные источники данных OLE DB связываются с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> объекта.  
  
 Серверы удаленной базы данных могут быть связаны для текущего экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью поставщика OLE DB. В SMO связанные серверы представлены <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> объекта. <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> Свойство ссылается на коллекцию <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> объектов. В них хранятся учетные данные входа, требуемые для установления соединения со связанным сервером.  
  
## <a name="ole-db-providers"></a>Поставщики OLE DB  
 В SMO установленные поставщики OLE DB представлены коллекцией объектов <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>.  
  
## <a name="example"></a>Пример  
 В следующем примере кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в разделе [Создание проекта SMO на Visual Basic в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) и [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-basic"></a>Создание ссылки на сервер поставщика OLE-DB в Visual Basic  
 В примере кода показано, как создать ссылку на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB разнородный источник данных с помощью <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> объекта. Путем указания [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как имя продукта, доступе к данным на связанном сервере с помощью [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщик OLE DB клиента, являющегося официальным поставщиком OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLinkedServers1](SMO How to#SMO_VBLinkedServers1)]  -->  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Создание ссылки на сервер поставщика OLE-DB в Visual C#  
 В примере кода показано, как создать ссылку на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB разнородный источник данных с помощью <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> объекта. Путем указания [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как имя продукта, доступе к данным на связанном сервере с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщик OLE DB клиента, являющегося официальным поставщиком OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
   Server srv = new Server();   
   //Create a linked server.   
   LinkedServer lsrv = default(LinkedServer);   
   lsrv = new LinkedServer(srv, "OLEDBSRV");   
   //When the product name is SQL Server the remaining properties are   
   //not required to be set.   
   lsrv.ProductName = "SQL Server";   
   lsrv.Create();   
}   
```  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-powershell"></a>Создание ссылки на сервер поставщика OLE-DB в PowerShell  
 В примере кода показано, как создать ссылку на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB разнородный источник данных с помощью <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> объекта. Путем указания [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как имя продукта, доступе к данным на связанном сервере с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщик OLE DB клиента, являющегося официальным поставщиком OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -argumentlist $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.   
$lsvr.ProductName = "SQL Server"  
  
#Create the Database Object  
$lsvr.Create()   
```  
  
  
