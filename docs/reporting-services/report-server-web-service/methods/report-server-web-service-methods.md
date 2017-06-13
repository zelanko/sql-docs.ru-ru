---
title: "Методы веб-службы сервера отчетов | Документы Microsoft"
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
- Report Server Web service, methods
- Web service [Reporting Services], methods
- XML Web service [Reporting Services], features
- Web service [Reporting Services], features
- Report Server Web service, features
- XML Web service [Reporting Services], methods
ms.assetid: ce5afa27-e90c-44a7-b204-098a065b3665
caps.latest.revision: 49
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ec79e5169ff32294cc68f5bee24c3df677d8b38b
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="report-server-web-service-methods"></a>Методы веб-службы сервера отчетов
  Веб-службы сервера отчетов содержат различные категории методов, основанных на функциях компонентов. Эти методы доступны через несколько конечных точек веб-служб (три для управления отчетами и одна для их выполнения), которые в свою очередь доступны как члены классов <xref:ReportService2010.ReportingService2010> и <xref:ReportExecution2005.ReportExecutionService>. Эти классы можно формировать с помощью средство класс прокси-сервера, например wsdl.exe, которая входит в состав [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK. Дополнительные сведения о веб-сервера отчетов служб и [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], в разделе [построение приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
## <a name="endpoints-and-methods"></a>Конечные точки и методы  
 В следующей таблице указаны конечные точки веб-службы сервера отчетов и категории методов, предоставленные конечной точкой <xref:ReportService2010.ReportingService2010>. Сведения о методах, доступных в других конечных точек см. в разделе [Технический справочник по &#40; Службы SSRS &#41; ](../../../reporting-services/technical-reference-ssrs.md).  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Конечные точки службы Web сервера отчетов](../../../reporting-services/report-server-web-service/methods/report-server-web-service-endpoints.md)|Содержит описание конечных точек для управления и выполнения, используемых веб-службой сервера отчетов.|  
|[Методы управления пространством имен сервера отчетов](../../../reporting-services/report-server-web-service/methods/report-server-namespace-management-methods.md)|Описывает методы управления базой данных сервера отчетов. В частности, эти методы позволяют управлять папками и ресурсами, а также настраивать свойства элемента.|  
|[Методы авторизации](../../../reporting-services/report-server-web-service/methods/authorization-methods.md)|Описывает методы управления задачами, ролями и политиками.|  
|[Источники данных и способы подключения](../../../reporting-services/report-server-web-service/methods/data-sources-and-connection-methods.md)|Описывает методы настройки и управления соединениями с источниками данных и учетными данными для отчетов.|  
|[Методы параметров отчета](../../../reporting-services/report-server-web-service/methods/report-parameters-methods.md)|Описывает методы задания и получения параметров отчетов.|  
|[Методы модели - веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/methods/model-methods-report-server-web-service.md)|Описывает методы, которые можно использовать для управления моделями.|  
|[Визуализация и методов выполнения](../../../reporting-services/report-server-web-service/methods/rendering-and-execution-methods.md)|Описывает методы управления выполнением, подготовкой к просмотру и кэшированием отчетов.|  
|[Методы журнала отчета](../../../reporting-services/report-server-web-service/methods/report-history-methods.md)|Описывает методы создания моментальных снимков журнала отчета и управления ими.|  
|[Методы планирования](../../../reporting-services/report-server-web-service/methods/scheduling-methods.md)|Описывает методы создания общих расписаний и планов обновления кэша, используемых сервером отчетов, и управления ими.|  
|[Методы подписки и доставки](../../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md)|Описывает методы создания и управления подписками и доставки отчетов.|  
|[Методы связанных отчетов](../../../reporting-services/report-server-web-service/methods/linked-reports-methods.md)|Описывает методы создания связанных отчетов и управления ими.|  
  
## <a name="see-also"></a>См. также:  
 [Доступ к API-Интерфейс SOAP](../../../reporting-services/report-server-web-service/accessing-the-soap-api.md)   
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Технический справочник по &#40; Службы SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
