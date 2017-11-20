---
title: "Программная загрузка и запуск локального пакета | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: run-manage-packages-programmatically
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Integration Services packages, running
- events [Integration Services], capturing
- packages [Integration Services], running
- loading packages programmatically
- Visual Basic [Integration Services]
- running packages [Integration Services]
- programmatically load and run packages [SSIS]
ms.assetid: 2f9fc1a8-a001-4c54-8c64-63b443725422
caps.latest.revision: 60
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 07ceb460488ca1973295b6b8e991948efe8b9d2a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="loading-and-running-a-local-package-programmatically"></a>Программная загрузка и запуск локального пакета
  Можно запустить [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакетов по мере необходимости или в заранее определенное время с помощью методов, описанных в [выполняемые пакеты](https://msdn.microsoft.com/library/ms141708(v=sql.110).aspx). Однако с помощью всего нескольких строк кода можно выполнить пакет из пользовательского приложения, такого как приложение Windows Forms, приложение командной строки, веб-форма ASP.NET, веб-служба или служба Windows.  
  
 В данном разделе рассматриваются следующие темы.  
  
-   Программная загрузка пакета.  
  
-   Программное выполнение пакета.  
  
 Все методы, используемые в этом разделе для загрузки и выполнения пакетов, требуют наличия ссылки на **Microsoft.SqlServer.ManagedDTS** сборки. После добавления ссылки в новый проект импортируйте <xref:Microsoft.SqlServer.Dts.Runtime> пространство имен с **с помощью** или **Imports** инструкции.  
  
## <a name="loading-a-package-programmatically"></a>Программная загрузка пакета  
 Чтобы загрузить хранящийся локально или удаленно пакет на локальный компьютер программным путем, вызовите один из перечисленных далее методов.  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Файл|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A>|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A>|  
  
> [!IMPORTANT]  
>  Методы класса <xref:Microsoft.SqlServer.Dts.Runtime.Application> для работы с хранилищем пакетов служб SSIS поддерживают только «.», localhost и имя сервера для локального сервера. Нельзя использовать имя «(local)».  
  
## <a name="running-a-package-programmatically"></a>Программное выполнение пакета  
 Разработка пользовательского приложения в управляемом коде, которое выполняет пакет на локальном компьютере, осуществляется следующим образом. Приведенные здесь шаги проиллюстрированы образцом приложения командной строки, приведенным далее.  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically"></a>Программное выполнение пакета на локальном компьютере  
  
1.  Запустите среду разработки Visual Studio и создайте новое приложение на языке программирования по своему выбору. В этом образце используется приложение командной строки. Однако выполнить пакет можно также из приложения Windows Forms, веб-формы ASP.NET, веб-службы или службы Windows.  
  
2.  На **проекта** меню, нажмите кнопку **добавить ссылку** и добавьте ссылку на **Microsoft.SqlServer.ManagedDTS.dll**. Нажмите кнопку **ОК**.  
  
3.  В Visual Basic использовать **Imports** инструкции или C# **с помощью** инструкцию, чтобы импортировать **Microsoft.SqlServer.Dts.Runtime** пространства имен.  
  
4.  Добавьте следующий код в подпрограмму main. В следующем примере представлено полное консольное приложения.  
  
    > [!NOTE]  
    >  Данный образец кода иллюстрирует загрузку пакета из файловой системы с помощью метода <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A>. Однако пакет можно загрузить также и из базы данных MSDB путем вызова метода <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A> или из пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] путем вызова метода <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A>.  
  
5.  Запустите проект. В образце кода выполняется пакет образца CalculatedColumns, который устанавливается вместе с образцами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Результат выполнения пакета отображается в консольном окне.  
  
### <a name="sample-code"></a>Образец кода  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, Nothing)  
    pkgResults = pkg.Execute()  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, null);  
      pkgResults = pkg.Execute();  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
## <a name="capturing-events-from-a-running-package"></a>Перехват событий в выполняющемся пакете  
 Когда пакет запускается программно, как показано в предыдущем образце, может понадобиться также перехватить ошибки и другие события, возникающие по мере выполнения пакета. Это можно сделать, добавив класс, порожденный из класса <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents>, и передав ссылку на этот класс при загрузке пакета. Хотя следующий пример перехватывает только событие <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents.OnError%2A>, существует много других событий, которые позволяет перехватывать класс <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents>.  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically-and-capture-package-events"></a>Программное выполнение пакета на локальном компьютере и перехват событий пакета  
  
1.  Пройдите по шагам в предыдущем примере, чтобы создать проект для этого примера.  
  
2.  Добавьте следующий код в подпрограмму main. В следующем примере представлено полное консольное приложения.  
  
3.  Запустите проект. В образце кода выполняется пакет образца CalculatedColumns, который устанавливается вместе с образцами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Результат выполнения пакета отображается в консольном окне вместе с сообщениями о любых возникших ошибках.  
  
### <a name="sample-code"></a>Образец кода  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    Dim eventListener As New EventListener()  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, eventListener)  
    pkgResults = pkg.Execute(Nothing, Nothing, eventListener, Nothing, Nothing)  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
  
Class EventListener  
  Inherits DefaultEvents  
  
  Public Overrides Function OnError(ByVal source As Microsoft.SqlServer.Dts.Runtime.DtsObject, _  
    ByVal errorCode As Integer, ByVal subComponent As String, ByVal description As String, _  
    ByVal helpFile As String, ByVal helpContext As Integer, _  
    ByVal idofInterfaceWithError As String) As Boolean  
  
    ' Add application–specific diagnostics here.  
    Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description)  
    Return False  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppWithEventsCS  
{  
  class MyEventListener : DefaultEvents  
  {  
    public override bool OnError(DtsObject source, int errorCode, string subComponent,   
      string description, string helpFile, int helpContext, string idofInterfaceWithError)  
    {  
      // Add application-specific diagnostics here.  
      Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description);  
      return false;  
    }  
  }  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      MyEventListener eventListener = new MyEventListener();  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, eventListener);  
      pkgResults = pkg.Execute(null, null, eventListener, null, null);  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о различиях между локальным и удаленным выполнением](../../integration-services/run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)   
 [Программная загрузка и запуск удаленного пакета](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [Загрузка выхода локального пакета](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  

