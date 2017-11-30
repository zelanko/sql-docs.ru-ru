---
title: "Методы планирования | Документы Майкрософт"
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
- schedules [Reporting Services], methods
- reports [Reporting Services], scheduling
- shared schedules [Reporting Services], methods
- methods [Reporting Services], scheduling
ms.assetid: 68ae13f9-d91e-4572-a82a-8fa42001569e
caps.latest.revision: "35"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f9babec18539dac85568a4b15461a1c04f768098
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="scheduling-methods"></a>Методы планирования
  Можно использовать эти методы для создания и управления общими расписаниями выполнения и доставки отчета, а также кэшировать планы обновления, используемые сервером отчетов.  
  
|Метод|Действие|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|Создает план обновления кэша для элемента.|  
|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|Создание нового общего расписания.|  
|<xref:ReportService2010.ReportingService2010.DeleteCacheRefreshPlan%2A>|Удаляет план обновления кэша.|  
|<xref:ReportService2010.ReportingService2010.DeleteSchedule%2A>|Удаление общего расписания по определенному идентификатору расписания.|  
|<xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|Возвращает свойства указанного плана обновления кэша.|  
|<xref:ReportService2010.ReportingService2010.GetScheduleProperties%2A>|Возвращение значений свойств общего расписания.|  
|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A>|Возвращает список планов обновления кэша, связанный с элементом каталога.|  
|<xref:ReportService2010.ReportingService2010.ListScheduledItems%2A>|Возвращает список элементов, связанных с общим расписанием.|  
|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|Возвращает список всех общих расписаний на сервер отчетов или на сайт SharePoint.|  
|<xref:ReportService2010.ReportingService2010.ListScheduleStates%2A>|Возвращает список поддерживаемых режимов расписания.|  
|<xref:ReportService2010.ReportingService2010.PauseSchedule%2A>|Приостанавливает выполнение данного расписания.|  
|<xref:ReportService2010.ReportingService2010.ResumeSchedule%2A>|Продолжение приостановленного общего расписания.|  
|<xref:ReportService2010.ReportingService2010.SetCacheRefreshPlanProperties%2A>|Задает свойства плана обновления кэша.|  
|<xref:ReportService2010.ReportingService2010.SetScheduleProperties%2A>|Задание значений свойств общего расписания.|  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-служба сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Методы веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [Технический справочник (службы SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
