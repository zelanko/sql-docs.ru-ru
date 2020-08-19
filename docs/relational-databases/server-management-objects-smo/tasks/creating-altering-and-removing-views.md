---
description: Создание, изменение и удаление представлений
title: Создание, изменение и удаление представлений
ms.custom: seo-dt-2019
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 92a8a04eee2be3fdfa34cb5c5118bea7e3dad7ec
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420188"
---
# <a name="creating-altering-and-removing-views"></a>Создание, изменение и удаление представлений
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]
  В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SMO представления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] представлены объектом <xref:Microsoft.SqlServer.Management.Smo.View>.  
  
 Свойство <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.View> определяет представление. Это эквивалентно использованию инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT для создания представления.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. [в статье Создание проекта Visual C&#35; SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a>Создание, изменение и удаление представления на языке Visual Basic  
 В этом образце кода показано создание представления двух таблиц с использованием внутреннего соединения. Представление создается с использованием текстового режима, поэтому для него необходимо задать свойство <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A>.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define a View object variable by supplying the parent database, view name and schema in the constructor.
Dim myview As View
myview = New View(db, "Test_View", "Sales")
'Set the TextHeader and TextBody property to define the view.
myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"
myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"
'Create the view on the instance of SQL Server.
myview.Create()
'Remove the view.
myview.Drop()
```
  
## <a name="creating-altering-and-removing-a-view-in-visual-c"></a>Создание, изменение и удаление представления на языке Visual C#  
 В этом образце кода показано создание представления двух таблиц с использованием внутреннего соединения. Представление создается с использованием текстового режима, поэтому для него необходимо задать свойство <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A>.  
  
```csharp  
{  
        //Connect to the local, default instance of SQL Server.   
        Server srv;   
        srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db;   
        db = srv.Databases["AdventureWorks2012"];   
        //Define a View object variable by supplying the parent database, view name and schema in the constructor.   
        View myview;   
        myview = new View(db, "Test_View", "Sales");   
        //Set the TextHeader and TextBody property to define the view.   
        myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS";   
        myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID";   
        //Create the view on the instance of SQL Server.   
        myview.Create();   
        //Remove the view.   
        myview.Drop();   
        }  
```  
  
## <a name="creating-altering-and-removing-a-view-in-powershell"></a>Создание, изменение и удаление представления в PowerShell  
 В этом образце кода показано создание представления двух таблиц с использованием внутреннего соединения. Представление создается с использованием текстового режима, поэтому для него необходимо задать свойство <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A>.  
  
```powershell   
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a View object variable by supplying the parent database, view name and schema in the constructor.   
$myview  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.View `  
-argumentlist $db, "Test_View", "Sales"  
  
# Set the TextHeader and TextBody property to define the view.   
$myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"  
$myview.TextBody ="SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"  
  
# Create the view on the instance of SQL Server.   
$myview.Create()  
  
# Remove the view.   
$myview.Drop();  
```  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.SqlServer.Management.Smo.View>  
  
  
