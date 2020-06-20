---
title: Использование связанных серверов в SMO | Документация Майкрософт
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
ms.openlocfilehash: 67bb9f002356e94f2546527aacae13b56768930d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85003534"
---
# <a name="using-linked-servers-in-smo"></a>Использование связанных серверов в объектах SMO
  Связанный сервер представляет источник данных OLE DB на удаленном сервере. Удаленные источники данных OLE DB связываются с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при помощи объекта <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>.  
  
 Удаленные серверы баз данных могут быть связаны с текущим экземпляром с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] помощью поставщика OLE DB. В SMO связанные серверы представлены объектом <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. Свойство <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> указывает на коллекцию объектов <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin>. В них хранятся учетные данные входа, требуемые для установления соединения со связанным сервером.  
  
## <a name="ole-db-providers"></a>Поставщики OLE DB  
 В SMO установленные поставщики OLE DB представлены коллекцией объектов <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>.  
  
## <a name="example"></a>Пример  
 В следующем примере кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в статьях [Создание проекта Visual Basic SMO в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) и [Создание проекта Visual C&#35; SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-basic"></a>Создание ссылки на сервер поставщика OLE-DB в Visual Basic  
 Пример кода показывает, как создать ссылку на разнородный источник данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. Указав в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] качестве имени продукта, доступ к данным на связанном сервере осуществляется с помощью [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB клиента, который является официальным поставщиком OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLinkedServers1](SMO How to#SMO_VBLinkedServers1)]  -->  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Создание ссылки на сервер поставщика OLE-DB в Visual C#  
 Пример кода показывает, как создать ссылку на разнородный источник данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB с помощью объекта <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. Если в качестве названия продукта указан [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , то доступ к данным на связанном сервере осуществляется с помощью поставщика OLE DB для клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , являющегося официальным поставщиком OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```csharp
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
  
```powershell
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -ArgumentList $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.
$lsvr.ProductName = "SQL Server"
  
#Create the Database Object  
$lsvr.Create()
```  
