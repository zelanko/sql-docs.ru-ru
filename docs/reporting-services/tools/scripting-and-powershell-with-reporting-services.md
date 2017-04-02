---
title: "Сценарии и PowerShell со службами Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "09/14/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "сценарии [службы Reporting Services]"
  - "Службы Reporting Services, сценарии"
  - "сценарии [службы Reporting Services]"
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 17
---
# Сценарии и PowerShell со службами Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] поддерживает целый ряд сценариев разработки и управления посредством скриптов, включая служебную программу командной строки rs.exe, командлеты PowerShell для серверов отчетов в режиме SharePoint и использование объектной модели [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] из PowerShell для режима SharePoint и собственного режима.  
  
-   Администратор может написать на языке [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] скрипт, который позволит автоматизировать развертывание установки сервера отчетов и управление ей. Администраторы также могут создавать и запускать скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] для создания, настройки и обновления базы данных сервера отчетов. Администраторы также могут использовать возможности записи и воспроизведения компонентов скрипта в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , чтобы автоматизировать стандартные задачи обслуживания.  
  
-   Разработчики могут создавать пользовательские приложения, включающие скрипты. Можно запустить скрипт, который выполнит вызовы к веб-службе сервера отчетов. Практически любая операция доступная в управляемом коде, может быть написана и в скрипте.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] поддерживает скрипт .NET [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] как язык скриптов, который можно обработать программой RS.exe, сервером скриптов, который выполняется на сервере отчетов.  
  
## Образцы и командлеты PowerShell в режиме SharePoint для служб Reporting Services  
 ![Содержимое, связанное с PowerShell](../../analysis-services/instances/install-windows/media/rs-powershellicon.png "Содержимое, связанное с PowerShell")  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включает [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] командлеты для администрирования сервера отчетов.  
  
-   [PowerShell cmdlets for Reporting Services SharePoint Mode](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) содержит следующие примеры.  
  
    -   Создайте приложение службы и прокси-сервер  
  
    -   Проверьте и обновите модуль доставки  
  
    -   Получение и задание свойств базы данных приложения служб Reporting Services, например времени ожидания базы данных  
  
    -   Расширения данных списка  
  
## Объектная модель служб Reporting Services и примеры отчетов Powershell  
 ![Содержимое, связанное с PowerShell](../../analysis-services/instances/install-windows/media/rs-powershellicon.png "Содержимое, связанное с PowerShell")  
  
 Вызов PowerShell основной объектной модели, в большинстве случаев допустимый для режима SharePoint и собственного режима, например при работе с миграцией и подписками, а также дополнительные сопутствующие примеры по работе с подписками в SQL15.  
  
-   [Использование PowerShell для смены и перечисления владельцев подписок служб Reporting Services и запуска подписки](../../reporting-services/subscriptions/manage subscription owners and run subscription - powershell.md).  
  
-   [Использование PowerShell для создания виртуальной машины Windows Azure с помощью сервера отчетов, работающего в собственном режиме](http://msdn.microsoft.com/library/azure/dn449661.aspx).  
  
-   См. раздел "Доступ к классам WMI с помощью PowerShell" в статье [Access the Reporting Services WMI Provider](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md).  
  
-   [Администрирование служб SSRS с помощью PowerShell](http://curah.microsoft.com/13107/how-to-administer-ssrs-using-powershell)  
  
## Образцы скриптов RS.exe  
  
-   [Sample Reporting Services rs.exe Script to Copy Content between Report Servers](../../reporting-services/tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
-   Дополнительные примеры скриптов, приложений и расширений см. в разделе [Примеры продуктов SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## См. также  
 [Служебная программа RS.exe (SSRS)](../../reporting-services/tools/rs-exe-utility-ssrs.md)   
 [Написание скриптов для задач развертывания и администрирования](../../reporting-services/tools/script-deployment-and-administrative-tasks.md)   
 [Создание скриптов с помощью программы rs.exe и веб-службы](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
  
  