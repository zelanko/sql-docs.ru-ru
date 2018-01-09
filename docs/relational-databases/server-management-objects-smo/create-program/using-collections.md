---
title: "Использование коллекций | Документы Microsoft"
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
helpviewer_keywords:
- SQL Server Management Objects, collections
- SMO [SQL Server], collections
- collections [SMO]
ms.assetid: 209eb175-2514-4de1-bc32-b2e6a469d945
caps.latest.revision: "49"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f35839db630e0066568360b2372451abd37b01a9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="using-collections"></a>Использование коллекций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Коллекция является список объектов образована тот же класс объектов и использующих один и тот же родительский объект. Объект коллекции всегда содержит имя типа объекта с суффиксом Collection. Например, для доступа к столбцам заданной таблицы используется тип <xref:Microsoft.SqlServer.Management.Smo.ColumnCollection>. Он содержит все объекты <xref:Microsoft.SqlServer.Management.Smo.Column>, принадлежащие одному и тому же объекту <xref:Microsoft.SqlServer.Management.Smo.Table>.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] **Для... Каждый** инструкции или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] **foreach** инструкции можно использовать для перебора каждого элемента коллекции.  
  
## <a name="examples"></a>Примеры  
Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Create Visual C# 35; Проект SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-basic"></a>Ссылка на объект с помощью коллекции в языке Visual Basic  
 Данный пример кода показано, как задать свойство столбца с помощью <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>, и <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> свойства. Эти свойства представляют собой коллекции, с помощью которых можно указать на конкретный объект при их использовании с именем объекта в качестве параметра. Имя и схема являются обязательными для <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> свойства объекта коллекции.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Modify a property using the Databases, Tables, and Columns collections to reference a column.
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("ModifiedDate").Nullable = True
'Call the Alter method to make the change on the instance of SQL Server.
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("ModifiedDate").Alter()
```
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-c"></a>Ссылка на объект с помощью коллекции в языке Visual C#  
 Данный пример кода показано, как задать свойство столбца с помощью <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>, и <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> свойства. Эти свойства представляют собой коллекции, с помощью которых можно указать на конкретный объект при их использовании с именем объекта в качестве параметра. Имя и схема являются обязательными для <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> свойства объекта коллекции.  
  
```csharp  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Modify a property using the Databases, Tables, and Columns collections to reference a column.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Nullable = true;   
//Call the Alter method to make the change on the instance of SQL Server.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Alter();   
}  
```  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-basic"></a>Последовательный перебор элементов коллекции на языке Visual Basic  
 Этот пример кода проходит по <xref:Microsoft.AnalysisServices.Server.Databases%2A> свойства коллекции и отображает все подключения к экземпляру базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
Dim count As Integer
Dim total As Integer
'Iterate through the databases and call the GetActiveDBConnectionCount method.
Dim db As Database
For Each db In srv.Databases
    count = srv.GetActiveDBConnectionCount(db.Name)
    total = total + count
    'Display the number of connections for each database.
    Console.WriteLine(count & " connections on " & db.Name)
Next
'Display the total number of connections on the instance of SQL Server.
Console.WriteLine("Total connections =" & total)
```
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-c"></a>Последовательный перебор элементов коллекции на языке Visual C#  
 Этот пример кода проходит по <xref:Microsoft.AnalysisServices.Server.Databases%2A> свойства коллекции и отображает все подключения к экземпляру базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```csharp  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
int count = 0;   
int total = 0;   
//Iterate through the databases and call the GetActiveDBConnectionCount method.   
Database db = default(Database);   
foreach ( db in srv.Databases) {   
  count = srv.GetActiveDBConnectionCount(db.Name);   
  total = total + count;   
  //Display the number of connections for each database.   
  Console.WriteLine(count + " connections on " + db.Name);   
}   
//Display the total number of connections on the instance of SQL Server.   
Console.WriteLine("Total connections =" + total);   
}   
```  
  
  
