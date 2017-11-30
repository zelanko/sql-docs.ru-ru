---
title: "Вызов методов веб-служб | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
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
- Web service [Reporting Services], SOAP
- Web service [Reporting Services], calls
- calling Web service
- Report Server Web service, SOAP
- XML Web service [Reporting Services], calls
- Report Server Web service, calls
- XML Web service [Reporting Services], SOAP
- SOAP [Reporting Services], calls
ms.assetid: f6f0c6e3-8bb5-4c44-9d19-1872edc72746
caps.latest.revision: "38"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: eae7dc1f7e673f332f5c85db89b9a247f0a36d35
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="calling-web-service-methods"></a>Вызов методов веб-служб
  Если для вызова операций веб-службы используется класс прокси платформы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], вызов выполняется с помощью методов этого класса. Эти методы работают аналогично любому другому методу в классе из библиотеки классов платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Все методы веб-служб доступны для открытого доступа, при котором необходимо указывать соответствующее число аргументов и типы аргументов. После создания экземпляра класса-посредника в проекте можно вызывать методы для выполнения операций с отчетами на сервере отчетов. В следующем коде на языке C# показано использование метода <xref:ReportService2010.ReportingService2010.ListChildren%2A> класса прокси <xref:ReportService2010.ReportingService2010>. Этот код используется для рекурсивного вызова веб-службы, которая возвращает массив объектов <xref:ReportService2010.CatalogItem>, содержащий список всех элементов в базе данных сервера отчетов:  
  
```vb  
Dim rs As New ReportingService2010()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
Dim items As CatalogItem() = rs.ListChildren("/", True)  
```  
  
```csharp  
ReportingService2010 rs = new ReportingService2010();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
CatalogItem[] items = rs.ListChildren("/", true);  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-служба сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Технический справочник (службы SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
