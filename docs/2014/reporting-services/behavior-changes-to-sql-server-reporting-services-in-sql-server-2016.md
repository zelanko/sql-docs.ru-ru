---
title: Изменения в работе SQL Server Reporting Services в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
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
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 91fa7a66981f3e36c7e25babffbf73dc2519a0c2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109937"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a>Изменения в работе служб SQL Server Reporting Services в выпуске SQL Server 2014
  В этом разделе описаны изменения в работе служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Изменения в работе затрагивают работу и взаимодействие компонентов в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] по сравнению с предыдущими версиями [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 В этом разделе:  
  
-   [SQL Server 2014 Reporting Services изменения в поведении](#bkmk_sql14)  
  
-   [Важные изменения в работе служб SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
-   [Изменения в работе служб SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services изменения поведения  
 Поведение служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]не изменилось.  
  
##  <a name="bkmk_rc0"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services изменения поведения  
 В этом разделе описаны изменения в работе служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a>Разрешение «Просмотр элементов» не загружает общие наборы данных (режим интеграции с SharePoint)  
 **Новое поведение:** Пользователи с разрешением SharePoint "Просмотр элементов" больше не могут скачивать содержимое Reporting Services общих наборов данных. Такое изменение поведения теперь согласуется с разрешениями "Просмотр элементов" для отчетов, источников данных и моделей. Пользователи с разрешением "Просмотр элементов" могут просматривать и выполнять отчеты, источники данных и модели, но не могут скачивать их содержимое.  
  
 **Предыдущее поведение:** Пользователи с разрешением "Просмотр элементов" SharePoint могут скачать содержимое Reporting Services общих наборов данных.  
  
 Дополнительные сведения об уровнях разрешений в режиме интеграции с SharePoint см. в разделе [Пользовательские разрешения и уровни разрешений](https://technet.microsoft.com/library/cc721640.aspx).  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a>Журналы трассировки сервера отчетов имеют новое расположение для режима интеграции с SharePoint (режим интеграции с SharePoint).  
 **Новое поведение:** Для сервера отчетов, установленного в режиме интеграции с SharePoint, журналы трассировки сервера отчетов будут находиться в папке%Programfiles%\Common Files\Microsoft Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles.  
  
 **Предыдущее поведение:** Журналы трассировки сервера отчетов найдены по пути, аналогичному следующему:%Програмфилесдир%\микрософт SQL Server\\<RS_instance> \reporting Services\LogFiles  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a>API-интерфейс SOAP GetServerConfigInfo больше не поддерживается (режим интеграции с SharePoint).  
 **Новое поведение**: используйте командлет PowerShell Get-SPRSServiceApplicationServers.  
  
 **Предыдущее поведение:** Клиенты могут разработать код клиента SOAP для непосредственного взаимодействия с [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] конечной точкой и вызвать жетрепортсерверконфигинфо ().  
  
### <a name="report-server-configuration-and-management-tools"></a>Средства настройки и управления конфигурацией сервера отчетов  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a>Диспетчер конфигурации не используется в режиме интеграции с SharePoint Mode  
 **Новое поведение:** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager больше не поддерживает серверы отчетов в режиме интеграции с SharePoint. Настройка служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции SharePoint теперь может быть выполнена через центр администрирования SharePoint, поэтому диспетчер конфигурации [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] больше не поддерживает режим интеграции с SharePoint. Диспетчер конфигурации теперь используется только для серверов отчетов в собственном режиме.  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a>Изменить режим работы сервера нельзя.  
 **Новое поведение:** Изменить режимы сервера нельзя. Если вы установили сервер отчетов для работы в собственном режиме, то нельзя его переключить или перенастроить на работу в режиме интеграции с SharePoint. Если вы установили сервер отчетов для работы в режиме интеграции с SharePoint, то можно переключить режим работы сервера отчетов на собственный режим.  
  
 **Предыдущее поведение:** Клиент устанавливает сервер [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отчетов в режиме интеграции с SharePoint. Если необходимо переключить сервер отчетов на собственный режим работы, клиент может открыть диспетчер конфигурации [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и изменить режим с помощью создания новой или соединения с существующей базой данных собственного режима. Клиент может также использовать диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для переключения в собственный режим из режима интеграции с SharePoint.  
  
##  <a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services изменения поведения  
 В этом разделе описаны изменения в работе служб [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Поскольку SQL Server 2008 R2 содержит изменения дополнительного номера версии по сравнению с SQL Server 2008, рекомендуется также просмотреть содержимое раздела по SQL Server 2008.  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a>Свойство SecureConnectionLevel в библиотеке поставщика WMI служб Reporting Services  
 В библиотеке [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]поставщика WMI для свойство **SecureConnectionLevel** позволяет `0`использовать значения,`1`,`2`,`3`и, `0` указывающие, что протокол SSL не требуется для всех методов веб-службы, `3` что указывает на то, что SSL требуется для всех методов веб-службы, а `1` также `2` для указания подмножеств методов веб-службы, требующих SSL. В [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]эти значения будут иметь лишь два возможных значения:  
  
-   
  `0` означает, что SSL не требуется ни одному методу веб-службы.  
  
-   Положительное целое число указывает, что SSL требуется для всех методов веб-служб.  
  
 Это изменение влияет на то, как сервер отчетов реагирует на запросы веб-службы. Например <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> , теперь возвращает Nothing, если **SecureConnectionLevel** <xref:ReportService2005.ReportingService2005> имеет значение 0, а все методы в `1`, если **SecureConnectionLevel** имеет значение, `2`или `3`.  
  
## <a name="see-also"></a>См. также:  
 [Новые возможности &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Устаревшие функции в SQL Server Reporting Services в SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [Неподдерживаемые функции для SQL Server Reporting Services в SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)   
 [Критические изменения в службах SQL Server Reporting Services в выпуске SQL Server «2014»](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
