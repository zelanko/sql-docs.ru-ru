---
title: Методы планирования | Документы Майкрософт
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
- schedules [Reporting Services], methods
- reports [Reporting Services], scheduling
- shared schedules [Reporting Services], methods
- methods [Reporting Services], scheduling
ms.assetid: 68ae13f9-d91e-4572-a82a-8fa42001569e
caps.latest.revision: 34
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 10513c14e2d9c65a210eee837ce3c23b21ff77aa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087554"
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
  
## <a name="see-also"></a>См. также  
 [Создание приложений с помощью веб-службы и .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-служба сервера отчетов](../report-server-web-service.md)   
 [Методы веб-службы сервера отчетов](report-server-web-service-methods.md)   
 [Технический справочник (службы SSRS)](../../technical-reference-ssrs.md)  
  
  