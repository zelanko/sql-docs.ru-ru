---
title: Урок 3. Доступ к веб-службы | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c3e4c198-ab35-4548-9471-1b4e6b6e5dfd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 09671f8880f9f7745359961d9c6c126a893d26a7
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56024835"
---
# <a name="lesson-3-accessing-the-web-service"></a>Урок 3. Доступ к веб-службе
  После добавления в проект ссылки на веб-службу сервера отчетов будет создан экземпляр класса-посредника этой веб-службы. Теперь можно получить доступ к методам веб-службы путем вызова методов класса-посредника. Когда приложение вызывает эти методы, код класса-посредника, сформированный средой [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , обеспечивает соединения между приложением и веб-службой.  
  
 Вначале нужно создать экземпляр класса-посредника веб-службы <xref:ReportService2010.ReportingService2010>. Затем с помощью класса-посредника нужно вызвать метод веб-службы <xref:ReportService2010.ReportingService2010.GetProperties%2A>. Вызов будет использован для получения имени и описания одного из образцов отчетов под названием Company Sales.  
  
> [!NOTE]  
>  Во время доступа к веб-службе, запущенной на сервере [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services, к пути «ReportServer» необходимо добавить выражение «$SQLExpress». Пример:  
>   
>  `http://<Server Name>/reportserver$sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-access-the-web-service"></a>Получение доступа к веб-службе  
  
1.  В первую очередь требуется добавить пространство имен в файл Program.cs (Module1.vb в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) с помощью добавления директивы `using` (`Imports` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) в файл кода. Если применить эту директиву, нет необходимости полностью уточнять типы пространства имен.  
  
2.  Чтобы сделать это, добавьте следующий код в начало файла с кодом:  
  
    ```vb  
    Imports System  
    Imports GetPropertiesSample.ReportService2010  
    ```  
  
    ```csharp  
    using System;  
    using GetPropertiesSample.ReportService2010;  
    ```  
  
3.  После добавления директивы пространства имен в файл кода необходимо ввести следующий код в описание главного метода приложения командной строки. При настройке свойства **Url** экземпляра веб-службы обязательно измените имя сервера:  
  
    ```vb  
    Sub Main()  
       Dim rs As New ReportingService2010  
       rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
       rs.Url = "http://<Server Name>/reportserver/reportservice2010.asmx"  
  
       Dim name As New [Property]  
       name.Name = "Name"  
  
       Dim description As New [Property]  
       description.Name = "Description"  
  
       Dim properties(1) As [Property]  
       properties(0) = name  
       properties(1) = description  
  
       Try  
          Dim returnProperties As [Property]() = rs.GetProperties( _  
             "/AdventureWorks 2012 Sample Reports/Company Sales 2012", properties)  
  
          Dim p As [Property]  
          For Each p In returnProperties  
              Console.WriteLine((p.Name + ": " + p.Value))  
          Next p  
  
       Catch e As Exception  
          Console.WriteLine(e.Message)  
       End Try  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
       ReportingService2010 rs = new ReportingService2010();  
       rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
       rs.Url = "http://<Server Name>/reportserver/reportservice2010.asmx";  
  
       Property name = new Property();  
       name.Name = "Name";  
  
       Property description = new Property();  
       description.Name = "Description";  
  
       Property[] properties = new Property[2];  
       properties[0] = name;  
       properties[1] = description;  
  
       try  
       {  
          Property[] returnProperties = rs.GetProperties(  
          "/AdventureWorks 2012 Sample Reports/Company Sales 2012",properties);  
  
          foreach (Property p in returnProperties)  
          {  
             Console.WriteLine(p.Name + ": " + p.Value);  
          }  
       }  
  
       catch (Exception e)  
       {  
          Console.WriteLine(e.Message);  
       }  
    }  
    ```  
  
4.  Сохраните решение.  
  
 В образце кода из этого пошагового руководства используется метод веб-службы <xref:ReportService2010.ReportingService2010.GetProperties%2A> для получения свойства образца отчета «Продажи компании в 2012 г.». <xref:ReportService2010.ReportingService2010.GetProperties%2A> Метод принимает два аргумента: имя отчета, для которого требуется извлечь сведения о свойствах, а также массив **Property []** объектов, содержащий имена свойств, значения которых требуется извлечь. Этот метод возвращает массив объектов **Property[]** , который содержит имена и значения свойств, указанных в аргументе свойств.  
  
> [!NOTE]  
>  Если в качестве аргумента свойств указать пустой массив **Property[]** , будут возвращены все доступные свойства.  
  
 В коде предыдущего примера используется метод <xref:ReportService2010.ReportingService2010.GetProperties%2A>, возвращающий имя и описание образца отчета «Продажи компании в 2012 г.». В этом коде используется цикл `foreach`, чтобы вывести свойства и значения на консоль.  
  
 Дополнительные сведения о создании и использовании класса-посредника для веб-службы сервера отчетов см. в разделе [Creating the Web Service Proxy](../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md).  
  
## <a name="see-also"></a>См. также  
 [Занятие 4. Запуск приложения &#40;VB VC&#35;&#41;](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md)   
 [Доступ к веб-службы сервера отчетов, с помощью Visual Basic или Visual c#&#35; &#40;учебник по службам SSRS&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
