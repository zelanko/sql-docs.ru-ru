---
title: Программное добавление задач | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- tasks [Integration Services], packages
- adding package tasks
ms.assetid: 5d4652d5-228c-4238-905c-346dd8503fdf
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a4496c35376a91ca0450a68a08087bac5e034725
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51641971"
---
# <a name="adding-tasks-programmatically"></a>Программное добавление задач
  Задачи могут быть добавлены в среде выполнения к объектам следующих типов.  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Package>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Sequence>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForLoop>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>  
  
 Эти классы рассматриваются как контейнеры, причем все они наследуют свойство <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSequence.Executables%2A>. Контейнеры могут содержать коллекцию задач, представляющих собой исполняемые объекты, которые обрабатываются средой выполнения во время выполнения контейнера. Порядок выполнения объектов в коллекции определяется любым набором <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> для каждой задачи в контейнерах. Элементы управления очередностью включают ветвление выполнения в зависимости от успеха, неудачи или завершения любого объекта <xref:Microsoft.SqlServer.Dts.Runtime.Executable> в коллекции.  
  
 Каждый контейнер имеет коллекцию <xref:Microsoft.SqlServer.Dts.Runtime.Executables>, которая содержит отдельные объекты <xref:Microsoft.SqlServer.Dts.Runtime.Executable>. Каждая исполняемая задача наследует и реализует методы <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A>. Эти два метода вызываются средой выполнения для обработки каждого объекта <xref:Microsoft.SqlServer.Dts.Runtime.Executable>.  
  
 Чтобы добавить задачу к пакету, необходим контейнер с существующей коллекцией <xref:Microsoft.SqlServer.Dts.Runtime.Executables>. В большинстве случаев задачей, добавляемой к коллекции, является пакет. Чтобы добавить новый исполняемый файл задачи в коллекцию для этого контейнера, необходимо вызвать метод <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A>. Этот метод имеет единственный параметр — строку, которая содержит специальное имя CLSID, PROGID, STOCK или свойство <xref:Microsoft.SqlServer.Dts.Runtime.TaskInfo.CreationName%2A> добавляемой задачи.  
  
## <a name="task-names"></a>Имена задач  
 Задачу можно указать по имени или идентификатору, но специальное имя **STOCK** представляет собой параметр, используемый чаще всего в методе <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A>. Чтобы добавить задачу к исполняемому файлу, обозначенному специальным именем **STOCK**, используйте следующий синтаксис:  
  
```csharp  
Executable exec = package.Executables.Add("STOCK:BulkInsertTask");  
  
```  
  
```vb  
Dim exec As Executable = package.Executables.Add("STOCK:BulkInsertTask")  
  
```  
  
 В следующем списке для каждой задачи показаны имена, которые используются после специального имени **STOCK**.  
  
-   ActiveXScriptTask  
  
-   BulkInsertTask  
  
-   ExecuteProcessTask  
  
-   ExecutePackageTask  
  
-   Exec80PackageTask  
  
-   FileSystemTask  
  
-   FTPTask  
  
-   MSMQTask  
  
-   PipelineTask  
  
-   ScriptTask  
  
-   SendMailTask  
  
-   SQLTask  
  
-   TransferStoredProceduresTask  
  
-   TransferLoginsTask  
  
-   TransferErrorMessagesTask  
  
-   TransferJobsTask  
  
-   TransferObjectsTask  
  
-   TransferDatabaseTask  
  
-   WebServiceTask  
  
-   WmiDataReaderTask  
  
-   WmiEventWatcherTask  
  
-   XMLTask  
  
 Если предпочтительным является более явный синтаксис или если задача, которую требуется добавить, не имеет специального имени STOCK, то можно добавить задачу к исполняемому файлу, используя ее длинное имя. Этот синтаксис требует, чтобы был также указан номер версии задачи.  
  
```csharp  
Executable exec = package.Executables.Add(  
  "Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask, " +  
  "Microsoft.SqlServer.ScriptTask, Version=10.0.000.0, " +  
  "Culture=neutral, PublicKeyToken=89845dcd8080cc91");  
```  
  
```vb  
Dim exec As Executable = package.Executables.Add( _  
  "Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask, " & _  
  "Microsoft.SqlServer.ScriptTask, Version=10.0.000.0, " & _  
  "Culture=neutral, PublicKeyToken=89845dcd8080cc91")  
```  
  
 Можно получить длинное имя для задачи программным путем без обязательного указания версии задачи с помощью свойства **AssemblyQualifiedName** класса, как показано в следующем примере. В этом примере необходима ссылка на сборку Microsoft.SqlServer.SQLTask.  
  
```csharp  
using Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask;  
...  
      Executable exec = package.Executables.Add(  
        typeof(Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask).AssemblyQualifiedName);  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask  
...  
    Dim exec As Executable = package.Executables.Add( _  
      GetType(Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask).AssemblyQualifiedName)  
```  
  
 В следующем примере кода показано, как создать коллекцию <xref:Microsoft.SqlServer.Dts.Runtime.Executables> из нового пакета, а затем добавить задачи "Файловая система" и "Массовая вставка" в коллекцию с использованием их специальных имен **STOCK**. В этом примере необходимы ссылки на сборки Microsoft.SqlServer.BulkInsertTask и Microsoft.SqlServer.FileSystemTask.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
using Microsoft.SqlServer.Dts.Tasks.BulkInsertTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      // Add a File System task to the package.  
      Executable exec1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileSystemTask = exec1 as TaskHost;  
      // Add a Bulk Insert task to the package.  
      Executable exec2 = p.Executables.Add("STOCK:BulkInsertTask");  
      TaskHost thBulkInsertTask = exec2 as TaskHost;  
  
      // Iterate through the package Executables collection.  
      Executables pExecs = p.Executables;  
      foreach (Executable pExec in pExecs)  
      {  
        TaskHost taskHost = (TaskHost)pExec;  
        Console.WriteLine("Type {0}", taskHost.InnerObject.ToString());  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
Imports Microsoft.SqlServer.Dts.Tasks.BulkInsertTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task to the package.  
    Dim exec1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileSystemTask As TaskHost = CType(exec1, TaskHost)  
    ' Add a Bulk Insert task to the package.  
    Dim exec2 As Executable = p.Executables.Add("STOCK:BulkInsertTask")  
    Dim thBulkInsertTask As TaskHost = CType(exec2, TaskHost)  
  
    ' Iterate through the package Executables collection.  
    Dim pExecs As Executables = p.Executables  
    Dim pExec As Executable  
    For Each pExec In pExecs  
      Dim taskHost As TaskHost = CType(pExec, TaskHost)  
      Console.WriteLine("Type {0}", taskHost.InnerObject.ToString())  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 **Образец вывода:**  
  
 `Type Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask`  
  
 `Type Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask`  
  
## <a name="taskhost-container"></a>Контейнер TaskHost  
 Класс <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> представляет собой контейнер, который не появляется в графическом пользовательском интерфейсе, но очень важен в программировании. Этот класс является оболочкой для каждой задачи. Задачи, добавляемые к пакету с помощью метода <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> как объекты <xref:Microsoft.SqlServer.Dts.Runtime.Executable>, могут быть приведены как объекты <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>. Если задача приведена как <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, появляется возможность использовать в задаче дополнительные свойства и методы. Кроме того, можно получить доступ к самой задаче с помощью свойства <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>. В зависимости от конкретных потребностей, может быть решено оставить задачу в качестве объекта <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, чтобы можно было использовать свойства задачи с помощью коллекции <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A>. Преимущество использования коллекции <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> состоит в том, что может быть написан более общий код. Если для задачи требуется весьма конкретный код, необходимо привести задачу к соответствующему ей объекту.  
  
 В следующем примере кода показано, как привести объект <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> (thBulkInsertTask), который содержит задачу <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>, к объекту <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>.  
  
```csharp  
BulkInsertTask myTask = thBulkInsertTask.InnerObject as BulkInsertTask;  
```  
  
```vb  
Dim myTask As BulkInsertTask = CType(thBulkInsertTask.InnerObject, BulkInsertTask)  
```  
  
 В следующем примере кода показано, как привести исполняемый файл к объекту <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, а затем с помощью свойства <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> определить, какого типа исполняемый файл содержится на этом узле.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
using Microsoft.SqlServer.Dts.Tasks.BulkInsertTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      // Add a File System task to the package.  
      Executable exec1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileSystemTask1 = exec1 as TaskHost;  
      // Add a Bulk Insert task to the package.  
      Executable exec2 = p.Executables.Add("STOCK:BulkInsertTask");  
      TaskHost thFileSystemTask2 = exec2 as TaskHost;  
  
      // Iterate through the package Executables collection.  
      Executables pExecs = p.Executables;  
      foreach (Executable pExec in pExecs)  
      {  
        TaskHost taskHost = (TaskHost)pExec;  
        if (taskHost.InnerObject is Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask)  
        {  
          // Do work with FileSystemTask here.  
          Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString());  
        }  
        else if (taskHost.InnerObject is Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask)  
        {  
          // Do work with BulkInsertTask here.  
          Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString());  
        }  
        // Add additional statements to check InnerObject, if desired.  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
Imports Microsoft.SqlServer.Dts.Tasks.BulkInsertTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task to the package.  
    Dim exec1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileSystemTask1 As TaskHost = CType(exec1, TaskHost)  
    ' Add a Bulk Insert task to the package.  
    Dim exec2 As Executable = p.Executables.Add("STOCK:BulkInsertTask")  
    Dim thFileSystemTask2 As TaskHost = CType(exec2, TaskHost)  
  
    ' Iterate through the package Executables collection.  
    Dim pExecs As Executables = p.Executables  
    Dim pExec As Executable  
    For Each pExec In pExecs  
      Dim taskHost As TaskHost = CType(pExec, TaskHost)  
      If TypeOf taskHost.InnerObject Is Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask Then  
        ' Do work with FileSystemTask here.  
        Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString())  
      ElseIf TypeOf taskHost.InnerObject Is Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask Then  
        ' Do work with BulkInsertTask here.  
        Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString())  
      End If  
      ' Add additional statements to check InnerObject, if desired.  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 **Образец вывода:**  
  
 `Found task of type Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask`  
  
 `Found task of type Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask`  
  
 Инструкция <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> возвращает исполняемый файл, который приведен к объекту <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, из вновь созданного объекта <xref:Microsoft.SqlServer.Dts.Runtime.Executable>.  
  
 Чтобы задать свойства или вызвать методы нового объекта, можно воспользоваться одним из двух способов.  
  
1.  Применить коллекцию <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>. Например, для получения свойства объекта применить инструкцию `th.Properties["propertyname"].GetValue(th))`. Чтобы задать свойство, использовать инструкцию `th.Properties["propertyname"].SetValue(th, <value>);`.  
  
2.  Привести свойство <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> к классу задачи. Например, чтобы привести задачу «Массовая вставка» к задаче <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> после ее добавления в пакет в качестве <xref:Microsoft.SqlServer.Dts.Runtime.Executable> и последующего приведения к <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, можно использовать оператор `BulkInsertTask myTask = th.InnerObject as BulkInsertTask;`.  
  
 Использование в коде класса <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> вместо приведения к классу, зависящему от задачи, предоставляет следующие преимущества.  
  
-   Поставщик <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> не требует ссылки на сборку в коде.  
  
-   Можно разрабатывать код общих подпрограмм, способных работать в любой задаче, поскольку нет необходимости знать имя задачи во время компиляции. Такие общие подпрограммы включают методы, в которых имя задачи передается методу, а код метода работает во всех задачах. Это удобный способ создания тестового кода.  
  
 Приведение от класса <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> к классу, зависящему от задачи, позволяет достичь следующих преимуществ:  
  
-   Проект разрабатывается в среде Visual Studio, поэтому обеспечивается возможность автоматического завершения инструкций (с помощью технологии IntelliSense).  
  
-   Код может работать быстрее.  
  
-   Объекты, зависящие от задачи, обеспечивают применение раннего связывания и завершающую оптимизацию. Дополнительные сведения о раннем и позднем связывании см. в подразделе «Раннее и позднее связывание» в разделе «Основные понятия языка Visual Basic».  
  
 В следующем примере кода раскрывается понятие повторного использования кода задачи. Вместо приведения задач к конкретным эквивалентным им классам в этом примере кода показано, как привести исполняемый файл к объекту <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, а затем воспользоваться коллекцией <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> для написания общего кода для всех задач.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package = new Package();  
  
      string[] tasks = { "STOCK:SQLTask", "STOCK:ScriptTask",   
        "STOCK:ExecuteProcessTask", "STOCK:PipelineTask",   
        "STOCK:FTPTask", "STOCK:SendMailTask", "STOCK:MSMQTask" };  
  
      foreach (string s in tasks)  
      {  
        TaskHost taskhost = package.Executables.Add(s) as TaskHost;  
        DtsProperties props = taskhost.Properties;  
        Console.WriteLine("Enumerating properties on " + taskhost.Name);  
        Console.WriteLine(" TaskHost.InnerObject is " + taskhost.InnerObject.ToString());  
        Console.WriteLine();  
  
        foreach (DtsProperty prop in props)  
        {  
          Console.WriteLine("Properties for " + prop.Name);  
          Console.WriteLine("Name : " + prop.Name);  
          Console.WriteLine("Type : " + prop.Type.ToString());  
          Console.WriteLine("Readable : " + prop.Get.ToString());  
          Console.WriteLine("Writable : " + prop.Set.ToString());  
          Console.WriteLine();  
        }  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Package = New Package()  
  
    Dim tasks() As String = New String() {"STOCK:SQLTask", "STOCK:ScriptTask", _  
              "STOCK:ExecuteProcessTask", "STOCK:PipelineTask", _  
              "STOCK:FTPTask", "STOCK:SendMailTask", "STOCK:MSMQTask"}  
  
    For Each s As String In tasks  
  
      Dim taskhost As TaskHost = CType(package.Executables.Add(s), TaskHost)  
      Dim props As DtsProperties = taskhost.Properties  
      Console.WriteLine("Enumerating properties on " & taskhost.Name)  
      Console.WriteLine(" TaskHost.InnerObject is " & taskhost.InnerObject.ToString())  
      Console.WriteLine()  
  
      For Each prop As DtsProperty In props  
        Console.WriteLine("Properties for " + prop.Name)  
        Console.WriteLine(" Name : " + prop.Name)  
        Console.WriteLine(" Type : " + prop.Type.ToString())  
        Console.WriteLine(" Readable : " + prop.Get.ToString())  
        Console.WriteLine(" Writable : " + prop.Set.ToString())  
        Console.WriteLine()  
      Next  
  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись в блоге [EzAPI — обновление для SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223) на сайте blogs.msdn.com.  

## <a name="see-also"></a>См. также:  
 [Соединение задач программным образом](../../integration-services/building-packages-programmatically/connecting-tasks-programmatically.md)  
  
  
