---
title: Использование коллекций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQL Server Management Objects, collections
- SMO [SQL Server], collections
- collections [SMO]
ms.assetid: 209eb175-2514-4de1-bc32-b2e6a469d945
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0be31e67be0b80de13a9239b221ca73436a8d6e7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63192120"
---
# <a name="using-collections"></a>Использование коллекций
  Коллекция — это список объектов одного и того же класса с одним и тем же родительским объектом. Объект коллекции всегда содержит имя типа объекта с суффиксом Collection. Например, для доступа к столбцам заданной таблицы используется тип <xref:Microsoft.SqlServer.Management.Smo.ColumnCollection>. Он содержит все объекты <xref:Microsoft.SqlServer.Management.Smo.Column>, принадлежащие одному и тому же объекту <xref:Microsoft.SqlServer.Management.Smo.Table>.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `For...Each` Инструкции или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] `foreach` инструкции можно перебирать все элементы коллекции.  
  
## <a name="examples"></a>Примеры  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-basic"></a>Ссылка на объект с помощью коллекции в языке Visual Basic  
 В данном примере кода демонстрируется задание свойства столбца с помощью свойств <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> и <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A>. Эти свойства представляют собой коллекции, с помощью которых можно указать на конкретный объект при их использовании с именем объекта в качестве параметра. Для свойства объекта коллекции <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> требуются имя и схема.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCollections1](SMO How to#SMO_VBCollections1)]  -->  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-c"></a>Ссылка на объект с помощью коллекции в языке Visual C#  
 В данном примере кода демонстрируется задание свойства столбца с помощью свойств <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> и <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A>. Эти свойства представляют собой коллекции, с помощью которых можно указать на конкретный объект при их использовании с именем объекта в качестве параметра. Для свойства объекта коллекции <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> требуются имя и схема.  
  
```  
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
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCollections2](SMO How to#SMO_VBCollections2)]  -->  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-c"></a>Последовательный перебор элементов коллекции на языке Visual C#  
 В данном примере кода выполняется итерация по коллекции <xref:Microsoft.AnalysisServices.Server.Databases%2A> и отображаются все подключения базы данных к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
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
  
  
