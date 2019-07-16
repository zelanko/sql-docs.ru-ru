---
title: Создание, изменение и удаление представлений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1f19027d4707220306accfe451314f52a22cfe35
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68211885"
---
# <a name="creating-altering-and-removing-views"></a>Создание, изменение и удаление представлений
  В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SMO представления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] представлены объектом <xref:Microsoft.SqlServer.Management.Smo.View>.  
  
 Свойство <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.View> определяет представление. Это эквивалентно использованию инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT для создания представления.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Создание проекта SMO на Visual Basic в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) или [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a>Создание, изменение и удаление представления на языке Visual Basic  
 В этом образце кода показано создание представления двух таблиц с использованием внутреннего соединения. Представление создается с использованием текстового режима, поэтому для него необходимо задать свойство <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A>.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBViews1](SMO How to#SMO_VBViews1)]  -->  
  
## <a name="creating-altering-and-removing-a-view-in-visual-c"></a>Создание, изменение и удаление представления на языке Visual C#  
 В этом образце кода показано создание представления двух таблиц с использованием внутреннего соединения. Представление создается с использованием текстового режима, поэтому для него необходимо задать свойство <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A>.  
  
```  
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
  
```  
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
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.SqlServer.Management.Smo.View>  
  
  
