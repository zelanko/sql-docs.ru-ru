---
title: Использование коллекций | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, collections
- SMO [SQL Server], collections
- collections [SMO]
ms.assetid: 209eb175-2514-4de1-bc32-b2e6a469d945
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3c3f4c31da84c2ca07b948faeba4aed7b93ad011
ms.sourcegitcommit: f3f83ef95399d1570851cd1360dc2f072736bef6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2019
ms.locfileid: "70148695"
---
# <a name="using-collections"></a>Использование коллекций
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Коллекция — это список объектов одного и того же класса с одним и тем же родительским объектом. Объект коллекции всегда содержит имя типа объекта с суффиксом Collection. Например, для доступа к столбцам заданной таблицы используется тип <xref:Microsoft.SqlServer.Management.Smo.ColumnCollection>. Он содержит все объекты <xref:Microsoft.SqlServer.Management.Smo.Column>, принадлежащие одному и тому же объекту <xref:Microsoft.SqlServer.Management.Smo.Table>.  
  
 С помощью инструкции [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] **vbprvb** или инструкции [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] **csprcs** можно перебирать все элементы коллекции.  
  
## <a name="examples"></a>Примеры  
Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. [в разделе Создание проекта Visual&#35; C SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-basic"></a>Ссылка на объект с помощью коллекции в языке Visual Basic  
 В данном примере кода демонстрируется задание свойства столбца с помощью свойств <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> и <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A>. Эти свойства представляют собой коллекции, с помощью которых можно указать на конкретный объект при их использовании с именем объекта в качестве параметра. Для свойства объекта коллекции <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> требуются имя и схема.  
  
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
 В данном примере кода демонстрируется задание свойства столбца с помощью свойств <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> и <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A>. Эти свойства представляют собой коллекции, с помощью которых можно указать на конкретный объект при их использовании с именем объекта в качестве параметра. Для свойства объекта коллекции <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> требуются имя и схема.  
  
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
 В данном примере кода выполняется итерация по коллекции <xref:Microsoft.AnalysisServices.Server.Databases%2A> и отображаются все подключения базы данных к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
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
 В данном примере кода выполняется итерация по коллекции <xref:Microsoft.AnalysisServices.Server.Databases%2A> и отображаются все подключения базы данных к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
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
  
  
