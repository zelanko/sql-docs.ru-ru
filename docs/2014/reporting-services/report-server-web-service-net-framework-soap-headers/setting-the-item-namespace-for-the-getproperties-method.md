---
title: Задание пространства имен элементов для метода GetProperties | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- item properties [Reporting Services]
- ItemNamespaceHeader SOAP header
- GetProperties method
ms.assetid: b0a08639-3101-40a2-abe2-3a41753826d1
caps.latest.revision: 37
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9cfe424d0cc39cb72c5d08215131a4cf540f2ed2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193735"
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
  
## <a name="see-also"></a>См. также  
 [Технический справочник (службы SSRS)](../technical-reference-ssrs.md)   
 [Использование заголовков SOAP в службах Reporting Services](using-reporting-services-soap-headers.md)  
  
  