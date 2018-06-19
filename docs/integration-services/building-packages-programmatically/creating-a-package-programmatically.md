---
title: Создание пакета программным образом | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: e44bcc70-32d3-43e8-a84b-29aef819d5d3
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 691f5c3cc96f1963116839dcaa846dbda4eae2fb
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35313063"
---
# <a name="creating-a-package-programmatically"></a>Создание пакета программным способом
  Объект <xref:Microsoft.SqlServer.Dts.Runtime.Package> представляет собой контейнер верхнего уровня для всех остальных объектов в решении служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Пакет, являющийся контейнером верхнего уровня, создается в качестве первого объекта, а последующие объекты добавляются в него и затем выполняются в контексте пакета. Сам пакет перемещения или преобразования данных не осуществляет. Для выполнения этих функций используются задачи, содержащиеся в пакете. Задачи выполняют основную работу пакета. Они определяют функциональность пакета. Пакет создается и выполняется всего тремя строками кода, однако к нему могут быть добавлены различные задачи и объекты <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>, что обеспечивает дополнительную функциональность пакета. В этом разделе описывается программное создание пакета. В нем не содержатся сведения о создании задач или диспетчера соединений <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>. Эти темы рассматриваются в последующих разделах.  
  
## <a name="example"></a>Пример  
 При написании кода с использованием интегрированной среды разработки Visual Studio IDE необходима ссылка на библиотеку Microsoft.SqlServer.ManagedDTS.DLL, на которую ссылается инструкция `using` (`Imports` в среде Visual Basic .NET), включающая пространство имен Microsoft.SqlServer.Dts.Runtime. В следующем образце кода демонстрируется создание пустого пакета.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package;  
      package = new Package();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Package  
    package = New Package  
  
  End Sub  
  
End Module  
```  
  
 Чтобы скомпилировать и выполнить образец, нажмите клавишу F5 в среде Visual Studio. Чтобы построить код с использованием компилятора C# **csc.exe** в командной строке, используйте следующие команды и ссылки на файлы, заменив заполнитель *\<имя_файла>* именем файла CS или VB и задав *\<имя_выходного_файла>* по своему усмотрению.  
  
 **csc /target:library /out: \<имя_выходного_файла>.dll \<имя_файла>.cs /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**  
  
 Чтобы выполнить сборку кода с помощью компилятора среды Visual Basic .NET **vbc.exe**, в командной строке используйте следующие команды и ссылки на файлы.  
  
 **vbc /target:library /out: \<имя_выходного_файла>.dll \<имя_файла>.vb /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**  
  
 Можно также создать пакет, загрузив существующий пакет, сохраненный на диске, в файловой системе или в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Отличие состоит в том, что сначала создается объект <xref:Microsoft.SqlServer.Dts.Runtime.Application>, а затем объект пакета заполняется одним из перегруженных методов приложения: методом **LoadPackage** для неструктурированных файлов, методом **LoadFromSQLServer** для пакетов, сохраненных в службах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или методом <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> для пакетов, сохраненных в файловой системе. В следующем примере с диска загружается существующий пакет, а затем просматриваются некоторые свойства этого пакета.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class ApplicationTests  
  {  
    static void Main(string[] args)  
    {  
      // The variable pkg points to the location of the  
      // ExecuteProcess package sample that was installed with  
      // the SSIS samples.  
      string pkg = @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx";  
  
      Application app = new Application();  
      Package p = app.LoadPackage(pkg, null);  
  
      // Now that the package is loaded, we can query on  
      // its properties.  
      int n = p.Configurations.Count;  
      DtsProperty p2 = p.Properties["VersionGUID"];  
      DTSProtectionLevel pl = p.ProtectionLevel;  
  
      Console.WriteLine("Number of configurations = " + n.ToString());  
      Console.WriteLine("VersionGUID = " + (string)p2.GetValue(p));  
      Console.WriteLine("ProtectionLevel = " + pl.ToString());  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module ApplicationTests  
  
  Sub Main()  
  
    ' The variable pkg points to the location of the  
    ' ExecuteProcess package sample that was installed with  
    ' the SSIS samples.  
    Dim pkg As String = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx"  
  
    Dim app As Application = New Application()  
    Dim p As Package = app.LoadPackage(pkg, Nothing)  
  
    ' Now that the package is loaded, we can query on  
    ' its properties.  
    Dim n As Integer = p.Configurations.Count  
    Dim p2 As DtsProperty = p.Properties("VersionGUID")  
    Dim pl As DTSProtectionLevel = p.ProtectionLevel  
  
    Console.WriteLine("Number of configurations = " & n.ToString())  
    Console.WriteLine("VersionGUID = " & CType(p2.GetValue(p), String))  
    Console.WriteLine("ProtectionLevel = " & pl.ToString())  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 **Образец вывода:**  
  
 `Number of configurations = 2`  
  
 `VersionGUID = {09016682-89B8-4406-AAC9-AF1E527FF50F}`  
  
 `ProtectionLevel = DontSaveSensitive`  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Запись в блоге [Образец API-интерфейса ― источник OleDB и назначение OleDB](http://go.microsoft.com/fwlink/?LinkId=220824) на сайте blogs.msdn.com.  
  
-   Запись в блоге [EzAPI — обновление для SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=243223) на сайте blogs.msdn.com.  
  
## <a name="see-also"></a>См. также:  
 [Программное добавление задач](../../integration-services/building-packages-programmatically/adding-tasks-programmatically.md)  
  
  
