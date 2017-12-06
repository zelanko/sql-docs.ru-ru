---
title: "Методы авторизации | Документы Майкрософт"
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
- security [Reporting Services], reports
- authorization [Reporting Services]
- reports [Reporting Services], security
- tasks [Reporting Services]
- roles [Reporting Services], methods
ms.assetid: 45e9cf2c-facf-4801-9482-c855403f42a8
caps.latest.revision: "42"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 91d3763a199950bb11d1c7c066a07ba16dfed6e3
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="authorization-methods"></a>Методы авторизации
  С помощью этих методов можно управлять задачами, ролями и политиками на сервере отчетов.  
  
|Метод|Действие|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateRole%2A>|Добавляет новую роль в базу данных сервера отчетов. Этот метод применим только в собственном режиме.|  
|<xref:ReportService2010.ReportingService2010.DeleteRole%2A>|Удаляет роль из базы данных сервера отчетов. Этот метод применим только в собственном режиме.|  
|<xref:ReportService2010.ReportingService2010.GetPermissions%2A>|Возвращает разрешения пользователя, связанные с данным элементом в базе данных сервера отчетов или библиотеке SharePoint.|  
|<xref:ReportService2010.ReportingService2010.GetPolicies%2A>|Возвращает политики, связанные с данным элементом в базе данных сервера отчетов или библиотеке SharePoint.|  
|<xref:ReportService2010.ReportingService2010.GetRoleProperties%2A>|Возвращает свойства метаданных роли и набор связанных задач.|  
|<xref:ReportService2010.ReportingService2010.GetSystemPermissions%2A>|Возвращает системные разрешения пользователя. Этот метод применим только в собственном режиме.|  
|<xref:ReportService2010.ReportingService2010.GetSystemPolicies%2A>|Возвращает системные политики, в том числе группы и роли, с которыми они связаны. Этот метод применим только в собственном режиме.|  
|<xref:ReportService2010.ReportingService2010.InheritParentSecurity%2A>|Удаляет политики, связанные с соответствующим элементом в базе данных сервера отчетов, и задает для элемента политики безопасности его родительского элемента.|  
|<xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>|Возвращает логическое значение, которое определяет, необходим ли протокол SSL (Secure Socket Layer) для использования конечной точки <xref:ReportService2010>.|  
|<xref:ReportService2010.ReportingService2010.ListRoles%2A>|Возвращает имена и описания ролей, управляемые сервером отчетов.|  
|<xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>|Возвращает список методов SOAP в конечной точке <xref:ReportExecution2005>, требующих при вызове безопасное соединение. Возвращаемые методы определяются с помощью параметра **SecureConnectionLevel** сервера отчетов.|  
|<xref:ReportService2010.ReportingService2010.ListTasks%2A>|Возвращает задания, управляемые сервером отчетов.|  
|<xref:ReportService2010.ReportingService2010.SetPolicies%2A>|Задает политики, связанные с указанным элементом.|  
|<xref:ReportService2010.ReportingService2010.SetRoleProperties%2A>|Задает свойства метаданных роли и связывает набор задач с этой ролью. Этот метод применим только в собственном режиме.|  
|<xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A>|Задает системную политику, которая определяет группы и связанные с ними роли. Этот метод применим только в собственном режиме.|  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-служба сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Методы веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [Технический справочник (службы SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
