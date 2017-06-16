---
title: "Модель методов - веб-служба сервера отчетов | Документы Microsoft"
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
ms.assetid: d3e658c9-bb22-480b-a3d5-bcde8f537ab2
caps.latest.revision: 4
author: sabotta
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 350614f2ba7d522860c15a27456598aeb12c270a
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="model-methods---report-server-web-service"></a>Методы модели - веб-службы сервера отчетов
  Эти методы можно использовать для управления моделями.  
  
|Метод|Действие|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GenerateModel%2A>|Создает модель по умолчанию на основе общего источника данных.|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPermissions%2A>|Получает разрешения пользователя, связанные с элементом модели.|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPolicies%2A>|Получает политики, связанные с элементом модели.|  
|<xref:ReportService2010.ReportingService2010.GetUserModel%2A>|Возвращает семантическую часть модели для текущего пользователя.|  
|<xref:ReportService2010.ReportingService2010.InheritModelItemParentSecurity%2A>|Удаляет политики, связанные с элементом модели, в результате чего элемент модели наследует политики от родительского элемента.|  
|<xref:ReportService2010.ReportingService2010.ListModelDrillthroughReports%2A>|Выводит список детализированных отчетов, связанных с сущностью модели.|  
|<xref:ReportService2010.ReportingService2010.ListModelItemChildren%2A>|Возвращает массив дочерних элементов элемента модели.|  
|<xref:ReportService2010.ReportingService2010.ListModelItemTypes%2A>|Возвращает список поддерживаемых типов элементов модели.|  
|<xref:ReportService2010.ReportingService2010.ListModelPerspectives%2A>|Выводит список моделей и перспектив, доступных пользователю.|  
|<xref:ReportService2010.ReportingService2010.RegenerateModel%2A>|Обновляет существующую модель на основе изменений схемы источника данных.|  
|<xref:ReportService2010.ReportingService2010.RemoveAllModelItemPolicies%2A>|Удаляет все политики, связанные с элементами модели в указанной модели.|  
|<xref:ReportService2010.ReportingService2010.SetModelDrillthroughReports%2A>|Связывает набор детализированных отчетов с моделью.|  
|<xref:ReportService2010.ReportingService2010.SetModelItemPolicies%2A>|Задает политики безопасности для элемента модели.|  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Методы веб-службы для сервера отчетов](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [Технический справочник (службы SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
