---
title: Использование связанных серверов в SMO | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d7c8ad7a4069ab35db2016a84279f80e707fad8f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892386"
---
# <a name="using-linked-servers-in-smo"></a>Использование связанных серверов в объектах SMO
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw.md)]

  Связанный сервер представляет источник данных OLE DB на удаленном сервере. Удаленные источники данных OLE DB связываются с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при помощи объекта <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>.  
  
 Удаленные серверы баз данных могут быть связаны с текущим экземпляром с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] помощью поставщика OLE DB. В SMO связанные серверы представлены объектом <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. Свойство <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> указывает на коллекцию объектов <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin>. В них хранятся учетные данные входа, требуемые для установления соединения со связанным сервером.  
  
## <a name="ole-db-providers"></a>Поставщики OLE DB  
 В SMO установленные поставщики OLE DB представлены коллекцией объектов <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>.  
  
## <a name="example"></a>Пример  
 В следующих примерах кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. [в статье Создание проекта Visual C&#35; SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
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
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -argumentlist $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.   
$lsvr.ProductName = "SQL Server"  
  
#Create the Database Object  
$lsvr.Create()   
```  
  
  
