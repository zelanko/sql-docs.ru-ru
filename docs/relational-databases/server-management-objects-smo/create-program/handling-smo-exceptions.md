---
title: "Обработка исключений SMO | Документы Microsoft"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
caps.latest.revision: "40"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6aa28e97c1fc20086dd03d1fc48173a02cde29d3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="handling-smo-exceptions"></a>Обработка исключений SMO
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]В управляемом коде исключения создаются при возникновении ошибки. Методы и свойства объектов SMO не сообщают об ошибке или успешном выполнении в возвращаемом значении. Исключения могут быть перехвачены и обработаны в обработчике исключений.  
  
 В объектах SMO существуют различные классы исключений. Сведения об исключении можно извлечь из свойств исключения, таких как свойство **Message** , которое предоставляет текстовое сообщение об исключении.  
  
 Инструкции обработки исключения зависят от конкретного языка программирования. Например, в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic это **перехватывать** инструкции.  
  
## <a name="inner-exceptions"></a>Внутренние исключения  
 Исключения могут быть общими и конкретными. Общие исключения содержат набор конкретных исключений. Несколько инструкций **Catch** можно использовать, чтобы обработать ожидаемые ошибки и позволить остальным ошибкам пройти через обработку общих исключений. Исключения часто происходят в каскадной последовательности. Часто исключение объекта SMO может быть вызвано исключением SQL. Чтобы это обнаружить, можно последовательно использовать свойство **InnerException** , чтобы определить исходное исключение, которое вызвало конечное исключение верхнего уровня.  
  
> [!NOTE]  
>  **SQLException** исключение объявляется в **System.Data.SqlClient** пространства имен.  
  
 ![Диаграмма, показывающая уровни, из которых могут поступать](../../../relational-databases/server-management-objects-smo/create-program/media/exception-flow.gif "диаграмма, показывающая уровни, из которых могут поступать исключения")  
  
 Диаграмма показывает поток исключений по уровням приложения.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Create Visual C# 35; Проект SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).
  
## <a name="catching-an-exception-in-visual-basic"></a>Перехват исключения на языке Visual Basic  
 Данный пример кода показывает, как использовать **Try... CATCH... Наконец** [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] инструкции для перехвата исключения объекта SMO. Все исключения объектов SMO имеют тип SmoException и перечислены в справке по объектам SMO. Последовательность внутренних исключений отображается, чтобы показать основание ошибки. Дополнительные сведения см. в разделе [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] документации по платформе .NET.  
  
```VBNET
'This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace is included.
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.
'Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.
Dim op As [Operator]
op = New [Operator](srv.JobServer, "Test_Operator")
op.Create()
'Start exception handling.
Try
    'Create the operator again to cause an SMO exception.
    Dim opx As OperatorCategory
    opx = New OperatorCategory(srv.JobServer, "Test_Operator")
    opx.Create()
    'Catch the SMO exception
Catch smoex As SmoException
    Console.WriteLine("This is an SMO Exception")
    'Display the SMO exception message.
    Console.WriteLine(smoex.Message)
    'Display the sequence of non-SMO exceptions that caused the SMO exception.
    Dim ex As Exception
    ex = smoex.InnerException
    Do While ex.InnerException IsNot (Nothing)
        Console.WriteLine(ex.InnerException.Message)
        ex = ex.InnerException
    Loop
    'Catch other non-SMO exceptions.
Catch ex As Exception
    Console.WriteLine("This is not an SMO exception.")
End Try
``` 
  
## <a name="catching-an-exception-in-visual-c"></a>Перехват исключения на языке Visual C#  
 В этом примере кода показано, как использовать инструкцию **Try…Catch…Finally** в Visual C# для перехвата исключения объекта SMO. Все исключения объектов SMO имеют тип SmoException и перечислены в справке по объектам SMO. Последовательность внутренних исключений отображается, чтобы показать основание ошибки. Дополнительные сведения см. в документации по языку Visual C#.  
  
```csharp  
{   
//This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace to be included.   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.   
//Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.   
op = new Operator(srv.JobServer, "Test_Operator");   
op.Create();   
//Start exception handling.   
try {   
    //Create the operator again to cause an SMO exception.   
    OperatorCategory opx;   
    opx = new OperatorCategory(srv.JobServer, "Test_Operator");   
    opx.Create();   
}   
//Catch the SMO exception   
catch (SmoException smoex) {   
    Console.WriteLine("This is an SMO Exception");   
   //Display the SMO exception message.   
   Console.WriteLine(smoex.Message);   
   //Display the sequence of non-SMO exceptions that caused the SMO exception.   
   Exception ex;   
   ex = smoex.InnerException;   
   while (!object.ReferenceEquals(ex.InnerException, (null))) {   
      Console.WriteLine(ex.InnerException.Message);   
      ex = ex.InnerException;   
    }   
    }   
   //Catch other non-SMO exceptions.   
   catch (Exception ex) {   
      Console.WriteLine("This is not an SMO exception.");   
}   
}  
```  
  
  
