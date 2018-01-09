---
title: "Создание, изменение и удаление представлений | Документы Microsoft"
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
helpviewer_keywords: views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cb90ebd600a17efc71c1195ed070091ca826fc4d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="creating-altering-and-removing-views"></a>Создание, изменение и удаление представлений
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] управляющих объектов (SMO) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] представлены представления <xref:Microsoft.SqlServer.Management.Smo.View> объекта.  
  
 Свойство <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.View> определяет представление. Он является эквивалентом [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкции SELECT для создания представления.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Create Visual C# 35; Проект SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a>Создание, изменение и удаление представления на языке Visual Basic  
 В этом образце кода показано создание представления двух таблиц с использованием внутреннего соединения. Представление создается с использованием текстового режима, поэтому <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> свойство должно быть задано.  
  
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
 В этом образце кода показано создание представления двух таблиц с использованием внутреннего соединения. Представление создается с использованием текстового режима, поэтому <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> свойство должно быть задано.  
  
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
 В этом образце кода показано создание представления двух таблиц с использованием внутреннего соединения. Представление создается с использованием текстового режима, поэтому <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> свойство должно быть задано.  
  
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
  
  
