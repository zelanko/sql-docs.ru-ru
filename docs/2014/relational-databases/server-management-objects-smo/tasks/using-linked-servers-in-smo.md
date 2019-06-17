---
title: Использование связанных серверов в объектах SMO | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 778da1b08aedd6c39db97351c6de799c883b6954
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63207029"
---
# <a name="using-linked-servers-in-smo"></a>Использование связанных серверов в объектах SMO
  Связанный сервер представляет источник данных OLE DB на удаленном сервере. Удаленные источники данных OLE DB связываются с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при помощи объекта <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>.  
  
 Удаленные серверы базы данных могут быть связаны с текущим экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью поставщика OLE DB. В SMO связанные серверы представлены объектом <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. Свойство <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> указывает на коллекцию объектов <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin>. В них хранятся учетные данные входа, требуемые для установления соединения со связанным сервером.  
  
## <a name="ole-db-providers"></a>Поставщики OLE DB  
 В SMO установленные поставщики OLE DB представлены коллекцией объектов <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>.  
  
## <a name="example"></a>Пример  
 В следующем примере кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в разделе [Создание проекта SMO на Visual Basic в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) и [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-basic"></a>Создание ссылки на сервер поставщика OLE-DB в Visual Basic  
 Пример кода показывает, как создать ссылку на разнородный источник данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. Если в качестве названия продукта указан [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , то доступ к данным на связанном сервере осуществляется с помощью поставщика OLE DB для клиента [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , являющегося официальным поставщиком OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLinkedServers1](SMO How to#SMO_VBLinkedServers1)]  -->  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Создание ссылки на сервер поставщика OLE-DB в Visual C#  
 Пример кода показывает, как создать ссылку на разнородный источник данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. Если в качестве названия продукта указан [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , то доступ к данным на связанном сервере осуществляется с помощью поставщика OLE DB для клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , являющегося официальным поставщиком OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
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
 Пример кода показывает, как создать ссылку на разнородный источник данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. Если в качестве названия продукта указан [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , то доступ к данным на связанном сервере осуществляется с помощью поставщика OLE DB для клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , являющегося официальным поставщиком OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
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
  
  
