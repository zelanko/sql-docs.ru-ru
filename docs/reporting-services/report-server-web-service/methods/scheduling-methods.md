---
title: Методы планирования | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: report-server-web-service
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- schedules [Reporting Services], methods
- reports [Reporting Services], scheduling
- shared schedules [Reporting Services], methods
- methods [Reporting Services], scheduling
ms.assetid: 68ae13f9-d91e-4572-a82a-8fa42001569e
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 20695ab30ea26c72b607fd217fc7fcaefab270fd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33025231"
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
  
  
