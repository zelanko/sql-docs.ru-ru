---
title: "Свойства служб Reporting Services | Документы Microsoft"
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- report servers [Reporting Services], properties
- properties [Reporting Services], about properties
- reports [Reporting Services], properties
- Report Server Web service, properties
- report properties [Reporting Services]
- XML Web service [Reporting Services], properties
- Web service [Reporting Services], properties
- properties [Reporting Services]
ms.assetid: 8c855194-4c20-4ecc-a328-5137d54b560c
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 3a81e521f0e17404ddfc0ed6d36950d8611ba666
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="reporting-services-properties"></a>Свойства служб Reporting Services
  Сервер отчетов определяет набор системных свойств, являющихся глобальными для сервера отчетов, и набор свойств элементов, связанных с отдельным элементом, хранимым в базе данных сервера отчетов. Свойства, определенные сервером отчетов, не могут быть удалены; в некоторых случаях они доступны только для чтения. Приложение может расширить системные свойства и свойства элементов, добавив к ним дополнительные определяемые пользователем свойства.  
  
 Следующие методы веб-службы, получить и задать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] свойства.  
  
|Метод|Действие|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|Возвращает значения одного или нескольких свойств элемента в базе данных сервера отчетов.|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|Возвращает одно или несколько системных свойств.|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|Задает одно или несколько свойств элемента в базе данных сервера отчетов.|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|Задает одно или несколько системных свойств.|  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Свойства элемента сервера отчетов](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-item-properties.md)|Описывает характерные для элементов свойства в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Системные свойства сервера отчетов](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)|Описывает характерные для системы свойства в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Технический справочник по &#40; Службы SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
