---
title: Установка свойств в SMO | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], properties
- SQL Server Management Objects, properties
- properties [SMO]
ms.assetid: 342569ba-d2f7-44d2-8f3f-ae9c701c7f0f
caps.latest.revision: 50
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c10da700c612c27883c4e4154583be742a22fef5
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43099513"
---
# <a name="setting-properties---smo"></a>Установка свойств в SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Свойства — это значения, которые хранят описательные сведения об объекте. Например [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] представлены параметры конфигурации <xref:Microsoft.SqlServer.Management.Smo.Server.Configuration%2A> свойств объекта. К свойствам можно получать как прямой, так и косвенный доступ при помощи коллекции свойств. Для прямого доступа к свойствам используется следующий синтаксис:  
  
 `objInstance.PropertyName`  
  
 Значение свойства можно изменить или получить в зависимости от того, доступно ли свойство для чтения и записи или только для чтения. Кроме того, некоторые свойства необходимо задавать перед тем, как можно будет создать объект. Дополнительные сведения о конкретном объекте см. в справочнике по объектам SMO.  
  
> [!NOTE]  
>  Коллекции дочерних объектов отображаются в виде свойства объекта. Например, коллекция **Tables** является свойством объекта **Server** . Дополнительные сведения см. в разделе [коллекций с помощью](../../../relational-databases/server-management-objects-smo/create-program/using-collections.md).  
  
 Свойства объекта являются элементами коллекции Properties. С помощью коллекции Properties можно просматривать все свойства объекта.  
  
 Иногда свойство недоступно по следующим причинам.  
  
-   Версия сервера не поддерживает это свойства (как при попытке получить доступ к свойству, которое представляет новую функцию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из более старой версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
-   Сервер не предоставляет данные для свойства, например, если при попытке доступа к свойству, которое представляет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] компонента, который не установлен.  
  
 Обрабатывать эти ситуации можно путем перехвата исключений SMO <xref:Microsoft.SqlServer.Management.Smo.UnknownPropertyException> и <xref:Microsoft.SqlServer.Management.Smo.PropertyCannotBeRetrievedException>.  
  
## <a name="setting-default-initialization-fields"></a>Задание полей инициализации по умолчанию  
 При получении объектов SMO выполняет оптимизацию. Оптимизация заключается в сведении к минимуму загружаемых свойств за счет автоматического масштабирования между следующими состояниями.  
  
1.  Частично загружено. При первой ссылке на объект выдается минимум свойств (например, имя и схема).  
  
2.  Полностью загружено. При ссылке на любое свойство остальные свойства, которые можно быстро загрузить, инициализируются и делаются доступными.  
  
3.  Свойства, использующие много памяти. Остальные недоступные свойства используют значительный объем памяти и иметь <xref:Microsoft.SqlServer.Management.Smo.Property.Expensive%2A> свойство значение true (такие как <xref:Microsoft.SqlServer.Management.Smo.Database.DataSpaceUsage%2A>). Эти свойства загружаются только тогда, когда на них производится ссылка.  
  
 Если приложение загружает дополнительные свойства помимо тех, которые представлены в состоянии частичной загрузки, оно отправляет запрос для получения этих дополнительных свойств и масштабируется до состояния полной загрузки. Это может привести к образованию ненужного трафика между клиентом и сервером. Дополнительную оптимизацию можно выполнить, вызвав <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> метод. Метод <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> позволяет создавать спецификацию свойств, которые загружаются при инициализации объекта.  
  
 Метод <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> задает поведение при загрузке свойств для остальной части приложения или до его сброса. Можно сохранить исходное поведение с помощью <xref:Microsoft.SqlServer.Management.Smo.Server.GetDefaultInitFields%2A> метод и восстановить его при необходимости.  
  
## <a name="examples"></a>Примеры  
Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  

  
## <a name="getting-and-setting-a-property-in-visual-basic"></a>Возвращение и задание свойства на языке Visual Basic  
 Данный пример кода показывает, как получить <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Information> объекта и как задать <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойства **ExecuteSql** членом <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> перечисления тип.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Get a property.
Console.WriteLine(srv.Information.Version)
'Set a property.
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql
```
  
## <a name="getting-and-setting-a-property-in-visual-c"></a>Возвращение и задание свойства на языке Visual C#  
 Данный пример кода показывает, как получить <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Information> объекта и как задать <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойства **ExecuteSql** членом <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> перечисления тип.  
  
```csharp  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Get a property.   
Console.WriteLine(srv.Information.Version);   
//Set a property.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-basic"></a>Задание различных свойств перед созданием объекта на языке Visual Basic  
 Данный пример кода показано, как непосредственная установка <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Table> , а также создание и добавление столбцов перед созданием <xref:Microsoft.SqlServer.Management.Smo.Table> объекта.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Create a new table in the AdventureWorks2012 database. 
Dim db As Database
db = srv.Databases("AdventureWorks2012")
Dim tb As Table
'Specify the parent database, table schema and the table name in the constructor.
tb = New Table(db, "Test_Table", "HumanResources")
'Add columns because the table requires columns before it can be created. 
Dim c1 As Column
'Specify the parent table, the column name and data type in the constructor.
c1 = New Column(tb, "ID", DataType.Int)
tb.Columns.Add(c1)
c1.Nullable = False
c1.Identity = True
c1.IdentityIncrement = 1
c1.IdentitySeed = 0
Dim c2 As Column
c2 = New Column(tb, "Name", DataType.NVarChar(100))
c2.Nullable = False
tb.Columns.Add(c2)
tb.AnsiNullsStatus = True
'Create the table on the instance of SQL Server.
tb.Create()
```
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-c"></a>Задание различных свойств перед созданием объекта на языке Visual C#  
 Данный пример кода показано, как непосредственная установка <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Table> , а также создание и добавление столбцов перед созданием <xref:Microsoft.SqlServer.Management.Smo.Table> объекта.  
  
```csharp  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Create a new table in the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
Table tb;   
//Specify the parent database, table schema, and the table name in the constructor.   
tb = new Table(db, "Test_Table", "HumanResources");   
//Add columns because the table requires columns before it can be created.   
Column c1;   
//Specify the parent table, the column name, and data type in the constructor.   
c1 = new Column(tb, "ID", DataType.Int);   
tb.Columns.Add(c1);   
c1.Nullable = false;   
c1.Identity = true;   
c1.IdentityIncrement = 1;   
c1.IdentitySeed = 0;   
Column c2;   
c2 = new Column(tb, "Name", DataType.NVarChar(100));   
c2.Nullable = false;   
tb.Columns.Add(c2);   
tb.AnsiNullsStatus = true;   
//Create the table on the instance of SQL Server.   
tb.Create();   
}  
```  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-basic"></a>Проход по всем свойствам объекта на языке Visual Basic  
 Этот пример кода проходит по **свойства** коллекцию <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> и отображает их на [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] результатов на экран.  
  
 В примере <xref:Microsoft.SqlServer.Management.Smo.Property> объекта была переведена в квадратные скобки, поскольку он также [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ключевое слово.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Set properties on the uspGetEmployeeManagers stored procedure on the AdventureWorks2012 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
Dim sp As StoredProcedure
sp = db.StoredProcedures("uspGetEmployeeManagers")
sp.AnsiNullsStatus = False
sp.QuotedIdentifierStatus = False
'Iterate through the properties of the stored procedure and display.
'Note the Property object requires [] parentheses to distinguish it from the Visual Basic key word.
Dim p As [Property]
For Each p In sp.Properties
    Console.WriteLine(p.Name & p.Value)
Next
```
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-c"></a>Проход по всем свойствам объекта на языке Visual C#  
 Этот пример кода проходит по **свойства** коллекцию <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> и отображает их на [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] результатов на экран.  
  
```csharp  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Set properties on the uspGetEmployeedManagers stored procedure on the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
StoredProcedure sp;   
sp = db.StoredProcedures("uspGetEmployeeManagers");   
sp.AnsiNullsStatus = false;   
sp.QuotedIdentifierStatus = false;   
//Iterate through the properties of the stored procedure and display.   
  Property p;   
  foreach ( p in sp.Properties) {   
    Console.WriteLine(p.Name + p.Value);   
  }   
}  
```  
  
## <a name="setting-default-initialization-fields-in-visual-basic"></a>Задание полей инициализации по умолчанию на языке Visual Basic  
 Этот пример кода демонстрирует, как свести к минимуму число свойств объекта, инициализируемых в программе SMO. Должен включать в себя `using System.Collections.Specialized`; инструкция, используемая <xref:System.Collections.Specialized.StringCollection> объекта.  
  
 При помощи приложения [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] можно сравнивать числовые инструкции, оправляемые экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], с этой оптимизацией.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Assign the Table object type to a System.Type object variable.
Dim tb As Table
Dim typ As Type
tb = New Table
typ = tb.GetType
'Assign the current default initialization fields for the Table object type to a 
'StringCollection object variable.
Dim sc As StringCollection
sc = srv.GetDefaultInitFields(typ)
'Set the default initialization fields for the Table object type to the CreateDate property.
srv.SetDefaultInitFields(typ, "CreateDate")
'Retrieve the Schema, Name, and CreateDate properties for every table in AdventureWorks2012.
'Note that the improvement in performance can be viewed in SQL Profiler.
For Each tb In db.Tables
    Console.WriteLine(tb.Schema + "." + tb.Name + " " + tb.CreateDate)
Next
'Set the default initialization fields for the Table object type back to the original settings.
srv.SetDefaultInitFields(typ, sc)
```
  
## <a name="setting-default-initialization-fields-in-visual-c"></a>Задание полей инициализации по умолчанию на языке Visual C#  
 Этот пример кода демонстрирует, как свести к минимуму число свойств объекта, инициализируемых в программе SMO. Должен включать в себя `using System.Collections.Specialized`; инструкция, используемая <xref:System.Collections.Specialized.StringCollection> объекта.  
  
 При помощи приложения [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] можно сравнивать числовые инструкции, оправляемые экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], с этой оптимизацией.  
  
```csharp  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Assign the Table object type to a System.Type object variable.   
Table tb;   
Type typ;   
tb = new Table();   
typ = tb.GetType;   
//Assign the current default initialization fields for the Table object type to a   
//StringCollection object variable.   
StringCollection sc;   
sc = srv.GetDefaultInitFields(typ);   
//Set the default initialization fields for the Table object type to the CreateDate property.   
srv.SetDefaultInitFields(typ, "CreateDate");   
//Retrieve the Schema, Name, and CreateDate properties for every table in AdventureWorks2012.   
   //Note that the improvement in performance can be viewed in SQL Server Profiler.   
foreach ( tb in db.Tables) {   
   Console.WriteLine(tb.Schema + "." + tb.Name + " " + tb.CreateDate);   
}   
//Set the default initialization fields for the Table object type back to the original settings.   
srv.SetDefaultInitFields(typ, sc);   
}  
```  
  
  
