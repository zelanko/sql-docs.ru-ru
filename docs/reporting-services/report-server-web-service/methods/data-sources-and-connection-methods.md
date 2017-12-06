---
title: "Источники данных и способы подключения | Документы Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: report-server-web-service
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- connections [Reporting Services], data sources
- reports [Reporting Services], data
- data sources [Reporting Services], methods
ms.assetid: 50999b52-fc7c-4333-9fb0-d04c37a4c90f
caps.latest.revision: "38"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2e8039303a6d21a3979a76d1a37aa0e041ba8eaa
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="data-sources-and-connection-methods"></a>Источники данных и методы соединения
  Эти методы можно использовать для установления и управления соединениями с источниками данных, а также учетными данными.  
  
|Метод|Действие|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateDataSource%2A>|Создает новый источник данных в базе данных сервера отчетов или библиотеке SharePoint.|  
|<xref:ReportService2010.ReportingService2010.DisableDataSource%2A>|Отключает включенный источник данных.|  
|<xref:ReportService2010.ReportingService2010.EnableDataSource%2A>|Включает отключенный источник данных.|  
|<xref:ReportService2010.ReportingService2010.GetDataSourceContents%2A>|Возвращает содержимое источника данных.|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSourcePrompts%2A>|Возвращает подсказку источника данных для указанного элемента.|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSources%2A>|Возвращает источники данных для элемента в каталоге.|  
|<xref:ReportService2010.ReportingService2010.ListDependentItems%2A>|Возвращает список элементов каталога, который ссылается на указанный элемент каталога.|  
|<xref:ReportService2010.ReportingService2010.ListSubscriptionsUsingDataSource%2A>|Возвращает список подписок, связанных с данным источником данных.|  
|<xref:ReportService2010.ReportingService2010.SetDataSourceContents%2A>|Задает свойства соединения, связанные с источником данных.|  
|<xref:ReportService2010.ReportingService2010.SetItemDataSources%2A>|Задает источники данных для элемента в базе данных сервера отчетов или библиотеке SharePoint.|  
|<xref:ReportService2010.ReportingService2010.TestConnectForDataSourceDefinition%2A>|Проверяет соединение с источником данных. Этот метод поддерживает непосредственную проверку источника данных.|  
|<xref:ReportService2010.ReportingService2010.TestConnectForItemDataSource%2A>|Проверяет соединение с источником данных. Этот метод поддерживает проверку опубликованных источников данных, используемых отчетами или моделями и общими источниками данных.|  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-служба сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Методы веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [Технический справочник (службы SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
