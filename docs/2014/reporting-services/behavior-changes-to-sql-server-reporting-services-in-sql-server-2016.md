---
title: Изменения в SQL Server Reporting Services в SQL Server 2014 | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Reporting Services, backward compatibility
- rows [Reporting Services], heights
- leading blanks
- installing Reporting Services, behavior changes with release
- cryptography [Reporting Services]
- Setup [Reporting Services], behavior changes with release
- DefaultValueQueryBased property
- encryption [Reporting Services]
- decryption [Reporting Services]
- blank characters [SQL Server]
- initializing installations [Reporting Services]
- behavior changes [Reporting Services]
ms.assetid: 2a767f0f-84f2-4099-8784-1e37790f858e
caps.latest.revision: 63
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 8f65fa1694cade07cbf33eec3a8b7afdc1c93280
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095636"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a>Изменения в работе служб SQL Server Reporting Services в выпуске SQL Server 2014
  В этом разделе описаны изменения в работе служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Изменения в работе затрагивают работу и взаимодействие компонентов в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] по сравнению с предыдущими версиями [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 В этом разделе:  
  
-   [SQL Server 2014 Reporting Services изменения в поведении](#bkmk_sql14)  
  
-   [SQL Server 2012 Reporting Services изменения в поведении](#bkmk_rc0)  
  
-   [SQL Server 2008 R2 Reporting Services изменения в поведении](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Изменения поведения Reporting Services  
 Существуют не [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] изменения в работе [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Изменения поведения Reporting Services  
 В этом разделе описаны изменения в работе служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a>Разрешение «Просмотр элементов» не загружает общие наборы данных (режим интеграции с SharePoint)  
 **Новые возможности.** Пользователи с разрешением «Просмотр элементов» в режиме интеграции с SharePoint не смогут больше скачивать содержимое общих наборов данных служб Reporting Services. Это изменение в работе теперь согласуется с разрешениями «Просмотр элементов» для отчетов, источников данных и моделей. Пользователи с разрешением «Просмотр элементов» могут просматривать и выполнять отчеты, источники данных и модели, но не могут загружать их содержимое.  
  
 **Возможности предыдущей версии.** Пользователи с разрешением «Просмотр элементов» в режиме интеграции с SharePoint могли скачивать содержимое общих наборов данных служб Reporting Services.  
  
 Дополнительные сведения об уровнях разрешений в режиме интеграции с SharePoint см. в разделе [Пользовательские разрешения и уровни разрешений](http://technet.microsoft.com/library/cc721640.aspx).  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a>Журналы трассировки сервера отчетов имеют новое расположение для режима интеграции с SharePoint (режим интеграции с SharePoint).  
 **Новое поведение:** для сервера отчетов, установленного в режиме интеграции с SharePoint, журналы трассировки сервера отчетов будет в каталоге %ProgramFiles%\common Files\Microsoft Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles.  
  
 **Прежнее поведение:** журналов трассировки сервера отчетов были найдены по пути, следующим образом: %Programfilesdir%\Microsoft SQL Server\\\Reporting Services\LogFiles < RS_instance >  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a>API-интерфейс SOAP GetServerConfigInfo больше не поддерживается (режим интеграции с SharePoint).  
 **Новое поведение**: использование командлета PowerShell «Get-SPRSServiceApplicationServers»  
  
 **Прежнее поведение:** клиенты могли разрабатывать код SOAP-клиента для взаимодействия непосредственно с [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] конечной точки и выполнять вызов GetReportServerConfigInfo().  
  
### <a name="report-server-configuration-and-management-tools"></a>Средства настройки и управления конфигурацией сервера отчетов  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a>Диспетчер конфигурации не используется в режиме интеграции с SharePoint Mode  
 **Новое поведение:** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager больше не поддерживает серверы отчетов в режиме интеграции с SharePoint. Конфигурация [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] режиме интеграции с SharePoint теперь может быть выполнена с помощью центра администрирования SharePoint и, следовательно, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager больше не поддерживает режим SharePoint. Диспетчер конфигурации теперь используется только для серверов отчетов в собственном режиме.  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a>Изменить режим работы сервера нельзя.  
 **Новые возможности.** Нельзя изменять режимы работы сервера. Если вы установили сервер отчетов для работы в собственном режиме, то нельзя его переключить или перенастроить на работу в режиме интеграции с SharePoint. Если вы установили сервер отчетов для работы в режиме интеграции с SharePoint, то можно переключить режим работы сервера отчетов на собственный режим.  
  
 **Прежнее поведение:** клиент устанавливает [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] сервера отчетов в режиме интеграции с SharePoint. Если необходимо переключить сервер отчетов на собственный режим работы, клиент может открыть диспетчер конфигурации [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и изменить режим с помощью создания новой или соединения с существующей базой данных собственного режима. Клиент также может использовать [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager для переключения из режима интеграции с SharePoint в собственный режим.  
  
##  <a name="bkmk_kj"></a> SQL Server 2008 R2 Reporting Services изменения в поведении  
 В этом разделе описаны изменения в [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Поскольку SQL Server 2008 R2 содержит изменения дополнительного номера версии по сравнению с SQL Server 2008, рекомендуется также просмотреть содержимое раздела по SQL Server 2008.  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a>Свойство SecureConnectionLevel в библиотеке поставщика WMI служб Reporting Services  
 В библиотеке поставщика WMI для [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], **SecureConnectionLevel** значения свойства `0`,`1`,`2`,`3`, с `0` означает, что Secure Socket Layer (SSL) не требуется ни одному методу веб-службы `3` , указывающее, что протокол SSL необходим для всех методов веб-службы, и `1` и `2` указывают подмножества методов веб-службы которым требуется SSL. В [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], эти значения будут иметь только два значения:  
  
-   `0` означает, что SSL не требуется ни одному методу веб-службы.  
  
-   Положительное целое число указывает, что SSL требуется для всех методов веб-служб.  
  
 Это изменение влияет на то, как сервер отчетов реагирует на запросы веб-службы. Например <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> теперь не возвращает ничего Если **SecureConnectionLevel** имеет значение 0, а также все методы в <xref:ReportService2005.ReportingService2005> Если **SecureConnectionLevel** имеет значение `1`, `2`, или `3`.  
  
## <a name="see-also"></a>См. также  
 [Новые возможности &#40;службы Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Устаревшие функции служб SQL Server Reporting Services в SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [Неподдерживаемые возможности в SQL Server Reporting Services в SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)   
 [Критические изменения в SQL Server Reporting Services в SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  