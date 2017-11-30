---
title: "Обработка предупреждений и ситуаций, не вызывающих исключений | Документы Майкрософт"
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- exceptions [Reporting Services], warnings that don't cause
- warnings [Reporting Services]
ms.assetid: 475c0713-6265-44e7-9ebc-ebdd1b89e0af
caps.latest.revision: "30"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ab2f3f1830cfd27f261446ca80a73b27126fa232
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="handling-warnings-and-cases-that-do-not-cause-exceptions"></a>Обработка предупреждений и ситуаций, не вызывающих исключения
  В службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] не формируются исключения применительно к предупреждениям и некоторым ошибкам. Например, при использовании метода <xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> с целью публикации нового отчета на сервере отчетов все возникающие предупреждения возвращаются в виде массива объектов <xref:ReportService2010.Warning>. Эти предупреждения должны быть обработаны и отображены, чтобы можно было осуществлять соответствующие действия.  
  
```vb  
Try  
   rs.CreateCatalogItem(name, parentFolder, False, definition, Nothing, warnings)  
  
   If Not (warnings.Length = 0) Then  
      Dim warning As Warning  
      For Each warning In warnings  
         Console.WriteLine(warning.Message)  
      Next warning  
   Else  
      Console.WriteLine("Report {0} created successfully with no warnings", name)  
   End If  
  
Catch ex As SoapException  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.CreateCatalogItem("Report", name, parentFolder, false, definition, null, out warnings);  
  
   if (warnings.Length != 0)  
   {  
      foreach (Warning warning in warnings)  
      {  
         Console.WriteLine(warning.Message);  
      }  
   }  
   else  
      Console.WriteLine("Report {0} created successfully with no warnings", name);  
}  
  
catch (SoapException ex)  
{  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
 Еще один способ обработки ошибок состоит в обработке возвращаемых значений определенных методов. К примеру, метод <xref:ReportService2010.ReportingService2010.FindItems%2A> можно использовать для поиска определенных элементов в базе данных сервера отчетов. Если элементы, соответствующие критериям поиска, не обнаружены, возвращается пустой массив объектов <xref:ReportService2010.CatalogItem>. Необходимо обработать этот массив, проверить его на наличие значений **NULL**, а если не обнаружены элементы, известить об этом пользователя.  
  
## <a name="see-also"></a>См. также:  
 <xref:ReportService2010.CatalogItem>   
 [Введение в обработку исключений в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Класс SoapException в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
