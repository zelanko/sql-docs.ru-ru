---
title: Добавление соединений программным образом | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- connection managers [Integration Services], packages
- Integration Services packages, connections
- connections [Integration Services], packages
- SSIS packages, connections
- packages [Integration Services], connections
- intrinsic properties [Integration Services]
- SQL Server Integration Services packages, connections
- ConnectionManager class
- SSIS connection managers
- adding package connections
ms.assetid: d90716d1-4c65-466c-b82c-4aabbee1e3e5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bcc954457c38f8c9bcd8e038ce3461bb94335eb0
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58274900"
---
# <a name="adding-connections-programmatically"></a>Добавление соединений программным образом
  Класс <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> представляет физические соединения с внешними источниками данных. Класс <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> изолирует данные о реализации соединения от среды выполнения. Это обеспечивает согласованное и прогнозируемое взаимодействие среды выполнения с каждым диспетчером соединений. Диспетчеры соединений содержат набор основных свойств, общих для всех соединений, например, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ID%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>. Однако, как правило, только свойства <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> требуются для настройки диспетчера соединений. Обычно классами подключения используются такие методы, как **Open** или **Connect** для установления физического соединения с источником данных, однако подсистема среды выполнения управляет всеми подключениями пакета во время его выполнения.  
  
 Класс <xref:Microsoft.SqlServer.Dts.Runtime.Connections> представляет собой коллекцию диспетчеров соединений, добавленных в этот пакет и доступных для использования во время выполнения. Можно добавить в коллекцию дополнительные диспетчеры соединений, используя метод <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> коллекции и указав строку, определяющую тип диспетчера соединений. Метод <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> возвращает экземпляр <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>, который был добавлен в пакет.  
  
## <a name="intrinsic-properties"></a>Важные свойства  
 Класс <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> представляет набор свойств, общих для всех соединений. Однако иногда может потребоваться доступ к уникальным свойствам, характеризующим определенный тип соединений. Коллекция <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Properties%2A> класса <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> обеспечивает доступ к таким свойствам. Свойства можно извлечь из коллекции с помощью индексатора или имени свойства и метода **GetValue**, а значения задаются с использованием метода **SetValue**. Свойства базового объекта соединения также можно задать, получив фактический экземпляр объекта и непосредственно определив его свойства. Чтобы получить базовое соединение, используйте свойство <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.InnerObject%2A> диспетчера соединений. Ниже приведена строка кода на языке C#, создающая диспетчер соединений ADO.NET, имеющий базовый класс <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.ConnectionManagerAdoNetClass>.  
  
 `ConnectionManagerAdoNetClass cmado = cm.InnerObject as ConnectionManagerAdoNet;`  
  
 Таким образом, выполняется приведение объекта управляемого диспетчера соединений к объекту его базового соединения. При использовании языка C++ вызывается метод **QueryInterface** объекта <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и запрашивается интерфейс объекта базового соединения.  
  
 В следующей таблице перечислены диспетчеры соединений, входящие в состав служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. и строка, которая используется в инструкции `package.Connections.Add("xxx")`. Список всех диспетчеров подключений см. в разделе [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md).  
  
|String|Диспетчер соединений|  
|------------|------------------------|  
|OLEDB|Диспетчер соединений для соединений OLE DB.|  
|ODBC|Диспетчер соединений для соединений ODBC.|  
|ADO|Диспетчер соединений для соединений ADO.|  
|ADO.NET:SQL|Диспетчер соединений для соединений ADO.NET (поставщик данных SQL).|  
|ADO.NET:OLEDB|Диспетчер соединений для соединений ADO.NET (поставщик данных OLE DB).|  
|FLATFILE|Диспетчер соединений для соединений неструктурированных файлов.|  
|FILE|Диспетчер соединений для соединений файлов.|  
|MULTIFLATFILE|Диспетчер соединений для соединений нескольких неструктурированных файлов.|  
|MULTIFILE|Диспетчер соединений для соединений нескольких файлов.|  
|SQLMOBILE|Диспетчер подключений для соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.|  
|MSOLAP100|Диспетчер соединений для соединений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|FTP|Диспетчер соединений для FTP-соединений.|  
|HTTP|Диспетчер соединений для HTTP-соединений.|  
|MSMQ|Диспетчер соединений для соединений службы очередей сообщений (MSMQ).|  
|SMTP|Диспетчер SMTP-соединений.|  
|«WMI»|Диспетчер соединений инструментария управления Windows (WMI-соединений).|  
  
 В следующем примере кода демонстрируется добавление соединений OLE DB и FILE в коллекцию <xref:Microsoft.SqlServer.Dts.Runtime.Package.Connections%2A> пакета <xref:Microsoft.SqlServer.Dts.Runtime.Package>. Затем в примере задаются свойства <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A>.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      // Create a package, and retrieve its connections.  
      Package pkg = new Package();  
      Connections pkgConns = pkg.Connections;  
  
      // Add an OLE DB connection to the package, using the   
      // method defined in the AddConnection class.  
      CreateConnection myOLEDBConn = new CreateConnection();  
      myOLEDBConn.CreateOLEDBConnection(pkg);  
  
      // View the new connection in the package.  
      Console.WriteLine("Connection description: {0}",  
         pkg.Connections["SSIS Connection Manager for OLE DB"].Description);  
  
      // Add a second connection to the package.  
      CreateConnection myFileConn = new CreateConnection();  
      myFileConn.CreateFileConnection(pkg);  
  
      // View the second connection in the package.  
      Console.WriteLine("Connection description: {0}",  
        pkg.Connections["SSIS Connection Manager for Files"].Description);  
  
      Console.WriteLine();  
      Console.WriteLine("Number of connections in package: {0}", pkg.Connections.Count);  
  
      Console.Read();  
    }  
  }  
  // <summary>  
  // This class contains the definitions for multiple  
  // connection managers.  
  // </summary>  
  public class CreateConnection  
  {  
    // Private data.  
    private ConnectionManager ConMgr;  
  
    // Class definition for OLE DB Provider.  
    public void CreateOLEDBConnection(Package p)  
    {  
      ConMgr = p.Connections.Add("OLEDB");  
      ConMgr.ConnectionString = "Provider=SQLOLEDB.1;" +  
        "Integrated Security=SSPI;Initial Catalog=AdventureWorks;" +  
        "Data Source=(local);";  
      ConMgr.Name = "SSIS Connection Manager for OLE DB";  
      ConMgr.Description = "OLE DB connection to the AdventureWorks database.";  
    }  
    public void CreateFileConnection(Package p)  
    {  
      ConMgr = p.Connections.Add("File");  
      ConMgr.ConnectionString = @"\\<yourserver>\<yourfolder>\books.xml";  
      ConMgr.Name = "SSIS Connection Manager for Files";  
      ConMgr.Description = "Flat File connection";  
    }  
  }  
  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    ' Create a package, and retrieve its connections.  
    Dim pkg As New Package()  
    Dim pkgConns As Connections = pkg.Connections  
  
    ' Add an OLE DB connection to the package, using the   
    ' method defined in the AddConnection class.  
    Dim myOLEDBConn As New CreateConnection()  
    myOLEDBConn.CreateOLEDBConnection(pkg)  
  
    ' View the new connection in the package.  
    Console.WriteLine("Connection description: {0}", _  
      pkg.Connections("SSIS Connection Manager for OLE DB").Description)  
  
    ' Add a second connection to the package.  
    Dim myFileConn As New CreateConnection()  
    myFileConn.CreateFileConnection(pkg)  
  
    ' View the second connection in the package.  
    Console.WriteLine("Connection description: {0}", _  
      pkg.Connections("SSIS Connection Manager for Files").Description)  
  
    Console.WriteLine()  
    Console.WriteLine("Number of connections in package: {0}", pkg.Connections.Count)  
  
    Console.Read()  
  
  End Sub  
  
End Module  
  
' This class contains the definitions for multiple  
' connection managers.  
  
Public Class CreateConnection  
  ' Private data.  
  Private ConMgr As ConnectionManager  
  
  ' Class definition for OLE DB provider.  
  Public Sub CreateOLEDBConnection(ByVal p As Package)  
    ConMgr = p.Connections.Add("OLEDB")  
    ConMgr.ConnectionString = "Provider=SQLOLEDB.1;" & _  
      "Integrated Security=SSPI;Initial Catalog=AdventureWorks;" & _  
      "Data Source=(local);"  
    ConMgr.Name = "SSIS Connection Manager for OLE DB"  
    ConMgr.Description = "OLE DB connection to the AdventureWorks database."  
  End Sub  
  
  Public Sub CreateFileConnection(ByVal p As Package)  
    ConMgr = p.Connections.Add("File")  
    ConMgr.ConnectionString = "\\<yourserver>\<yourfolder>\books.xml"  
    ConMgr.Name = "SSIS Connection Manager for Files"  
    ConMgr.Description = "Flat File connection"  
  End Sub  
  
End Class  
```  
  
 **Образец вывода:**  
  
 `Connection description: OLE DB connection to the AdventureWorks database.`  
  
 `Connection description: Flat File connection.`  
  
 `Number of connections in package: 2`  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Техническая статья [Строки подключения](https://go.microsoft.com/fwlink/?LinkId=220743) на сайте carlprothman.net.  
  
## <a name="see-also"></a>См. также:  
 [Соединения в службах Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [Создание диспетчеров соединений](https://msdn.microsoft.com/library/6ca317b8-0061-4d9d-b830-ee8c21268345)  
  
  
