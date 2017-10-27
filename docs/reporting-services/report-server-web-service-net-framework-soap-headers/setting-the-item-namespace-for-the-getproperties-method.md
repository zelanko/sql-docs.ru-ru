---
title: "Задание пространства имен элементов для метода GetProperties | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- item properties [Reporting Services]
- ItemNamespaceHeader SOAP header
- GetProperties method
ms.assetid: b0a08639-3101-40a2-abe2-3a41753826d1
caps.latest.revision: 38
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 6c47c200899dbd25c9685817ea81a391364739c6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="setting-the-item-namespace-for-the-getproperties-method"></a>Задание пространства имен элементов для метода GetProperties
  Заголовок SOAP <xref:ReportService2010.ItemNamespaceHeader> в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] служит для получения свойств элементов по двум различным идентификаторам элементов: полному пути к элементу и идентификатору элемента.  
  
 Во время вызова метода <xref:ReportService2010.ReportingService2010.GetProperties%2A> в качестве аргумента обычно передается полный путь к элементу, свойства которого нужно получить. Класс <xref:ReportService2010.ItemNamespaceHeader> позволяет задать заголовок SOAP для вызова метода, чтобы позволить использовать метод <xref:ReportService2010.ReportingService2010.GetProperties%2A>, передавая идентификатор элемента в качестве идентификатора.  
  
 В следующем образце кода значения свойств элемента возвращаются на основании идентификатора элемента.  
  
> [!NOTE]  
>  По умолчанию не нужно задавать значение <xref:ReportService2010.ItemNamespaceHeader>, если методу <xref:ReportService2010.ReportingService2010.GetProperties%2A> в качестве идентификатора элемента передается полное имя пути.  
  
```vb  
Imports System  
Imports System.Collections  
  
Class Sample  
   Sub Main()  
      Dim rs As New ReportingService2010()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      rs.Url = "http://<Server Name>/reportserver/ReportService2010.asmx"  
  
      Dim items() As CatalogItem  
  
      Try  
         ' Need the ID property of items. Normally, you would already have   
         ' this stored somewhere.  
         items = rs.ListChildren("/AdventureWorks Sample Reports", False)  
  
         ' Set the item namespace header to be GUID-based  
         rs.ItemNamespaceHeaderValue = New ItemNamespaceHeader()  
         rs.ItemNamespaceHeaderValue.ItemNamespace = ItemNamespaceEnum.GUIDBased  
  
         ' Call GetProperties with item ID.  
         If Not (items Is Nothing) Then  
            Dim item As CatalogItem  
            For Each item In  items  
               Dim properties As [Property]() = rs.GetProperties(item.ID, Nothing)  
               Dim property As [Property]  
               For Each property In  properties  
                  Console.WriteLine(([property].Name + ": " + [property].Value))  
               Next property  
               Console.WriteLine()  
            Next item  
         End If  
  
      Catch e As Exception  
         Console.WriteLine((e.Message + ": " + e.StackTrace))  
      End Try  
   End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.Collections;  
  
class Sample  
{  
   static void Main()  
   {  
   ReportingService2010 rs = new ReportingService2010();  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      rs.Url = "http://<Server Name>/reportserver/ReportService2010.asmx";  
  
      CatalogItem[] items;  
  
      try  
      {  
         // Need the ID property of items. Normally, you would already have   
         // this stored somewhere.  
         items = rs.ListChildren("/AdventureWorks Sample Reports", false);  
  
         // Set the item namespace header to be GUID-based  
         rs.ItemNamespaceHeaderValue = new ItemNamespaceHeader();  
         rs.ItemNamespaceHeaderValue.ItemNamespace = ItemNamespaceEnum.GUIDBased;  
  
         // Call GetProperties with item ID.  
         if (items != null)  
         {  
            foreach( CatalogItem item in items)  
            {  
               Property[] properties = rs.GetProperties(item.ID, null);  
               foreach (Property property in properties)  
               {  
                  Console.WriteLine(property.Name + ": " + property.Value);  
               }  
               Console.WriteLine();  
            }  
         }  
      }  
  
      catch (Exception e)  
      {  
         Console.WriteLine(e.Message);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Технический справочник по &#40; Службы SSRS &#41;](../../reporting-services/technical-reference-ssrs.md)   
 [Использование службы Reporting Services заголовки SOAP](../../reporting-services/report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)  
  
  

