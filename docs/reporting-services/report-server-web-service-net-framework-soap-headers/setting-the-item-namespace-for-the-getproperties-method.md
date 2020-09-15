---
description: Задание пространства имен элементов для метода GetProperties
title: Задание пространства имен элементов для метода GetProperties | Документы Майкрософт
Description: Узнайте, как получить свойства, основанные либо на пути, либо на идентификаторе элемента, используя метод GetProperties и заголовок SOAP ItemNamespaceHeader.
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-soap-headers
ms.topic: reference
helpviewer_keywords:
- item properties [Reporting Services]
- ItemNamespaceHeader SOAP header
- GetProperties method
ms.assetid: b0a08639-3101-40a2-abe2-3a41753826d1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fc0d61726a885b6a2422a4fe048121e65b8642f8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423248"
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
      rs.Url = "https://<Server Name>/reportserver/ReportService2010.asmx"  
  
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
      rs.Url = "https://<Server Name>/reportserver/ReportService2010.asmx";  
  
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
 [Технический справочник (службы SSRS)](../../reporting-services/technical-reference-ssrs.md)   
 [Использование заголовков SOAP служб Reporting Services](../../reporting-services/report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)  
  
  
