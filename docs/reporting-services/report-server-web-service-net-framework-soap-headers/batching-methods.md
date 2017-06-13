---
title: "Методы пакетной обработки | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- methods [Reporting Services], batches
- BatchHeader SOAP header
- Web service [Reporting Services], methods
- Report Server Web service, batching
- batches [Reporting Services]
- XML Web service [Reporting Services], methods
- locking [Reporting Services]
- multiple Web service methods
ms.assetid: 86435534-c9fe-4b49-b88c-7fb6d21976b0
caps.latest.revision: 36
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8b08c9f44efd416e3d5c9f24cb54f74569ba2882
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="batching-methods"></a>Методы пакетной работы
  Использование заголовков SOAP в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] позволяет включать в одну операцию несколько методов веб-служб. Методы выполняются в области одной транзакции базы данных, в порядке их вызова.  
  
 Одним из преимуществ использования пакетных методов с множественными операциями является возможность реализации отката. Если во время выполнения пакета в любом из вызовов методов возникнет ошибка, то сервер отчетов прекратит выполнение пакета и выполнит откат любых предыдущих операций. Это полезно в том случае, если выполнение вызова метода зависит от успешного завершения других вызовов метода в данном пакете.  
  
 Веб-служба не предоставляет семантики блокировки для пакетных операций с несколькими методами. Строки в базе данных сервера отчетов не блокируются для обновления до тех пор, пока сообщение не будет отправлено на сервер и не будет вызвана команда Execute.  
  
 Также не существует управления параллелизмом, которое гарантировало бы неизменность базы данных с момента последнего считывания. Если два клиента изменяют один и тот же элемент, тот более позднее обновление будет успешно выполнено в случае, если параметры все еще действительны (например, если элемент не был переименован).  
  
 В следующем примере метод <xref:ReportService2005.ReportingService2005.CreateFolder%2A> вызывается три раза; данные вызовы выполняются как один пакет. Если любой из вызовов метода <xref:ReportService2005.ReportingService2005.CreateFolder%2A> завершается неудачно, то отменяется весь пакет.  
  
```vb  
Imports System  
Imports System.Web.Services.Protocols  
Imports myNamespace.MyReferenceName  
  
Class Sample  
    Sub Main(args() As String)  
        Dim rs As New ReportingService2005()  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      ' Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        Dim bh As New BatchHeader()  
  
        bh.BatchId = service.CreateBatch()  
        rs.BatchHeaderValue = bh  
        rs.CreateFolder("New Folder1", "/", Nothing)  
        rs.CreateFolder("New Folder2", "/", Nothing)  
        rs.CreateFolder("New Folder3", "/", Nothing)  
  
        Console.WriteLine("Creating folders...")  
        rs.BatchHeaderValue = bh  
        rs.ExecuteBatch()  
        Console.WriteLine("Folders created successfully.")  
  
        rs.BatchHeaderValue = Nothing  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Web.Services.Protocols;   
using myNamespace.MyReferenceName;  
  
class Sample  
{  
    static void Main(string[] args)  
    {  
        ReportingService2005 rs = new ReportingService2005();  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      // Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        BatchHeader bh = new BatchHeader();  
  
        bh1.BatchID = service.CreateBatch();  
        rs.BatchHeaderValue = bh;  
        rs.CreateFolder("New Folder1", "/", null);  
        rs.CreateFolder("New Folder2", "/", null);  
        rs.CreateFolder("New Folder3", "/", null);  
  
        Console.WriteLine("Creating folders...");  
        rs.BatchHeaderValue = bh1;  
        rs.ExecuteBatch();  
        Console.WriteLine("Folders created successfully.");  
  
        rs.BatchHeaderValue = null;  
    }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 <xref:ReportService2005.ReportingService2005.CancelBatch%2A>   
 <xref:ReportService2005.ReportingService2005.CreateBatch%2A>   
 [Технический справочник по &#40; Службы SSRS &#41;](../../reporting-services/technical-reference-ssrs.md)   
 [Использование службы Reporting Services заголовки SOAP](../../reporting-services/report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)  
  
  
