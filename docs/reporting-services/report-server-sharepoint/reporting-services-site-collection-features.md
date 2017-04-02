---
title: "Компоненты семейства веб-сайтов служб Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
caps.latest.revision: 8
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Компоненты семейства веб-сайтов служб Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint предоставляют три компонента коллекции сайтов SharePoint. Эти компоненты поддерживают среду создания отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint — [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], компонент надстройки служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition и операции управления для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в центре администрирования SharePoint.  
  
## Компоненты семейства веб-сайтов  
 В следующей таблице приводится описание компонентов семейства веб-сайтов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
|Компонент|Description|  
|-------------|-----------------|  
|**Центр администрирования сервера отчетов**|Включает возможности для управления процессом интеграции с сервером отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Этот компонент устанавливается и используется в семействе веб-сайтов центра администрирования SharePoint.<br /><br /> Компонент интеграции сервера отчетов автоматически активируется в семействе веб-сайтов центра администрирования SharePoint после установки надстройки служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] для продуктов SharePoint. В некоторых ситуациях потребуется активировать этот компонент вручную. Чтобы активировать компонент сервера отчетов, используйте страницы служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на странице параметров сайта в центре администрирования SharePoint.<br /><br /> Версия служб [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и более поздние версии надстройки для продуктов SharePoint активируют функцию интеграции сервера отчетов для всех существующих на момент установки надстройки семейств веб-сайтов. Кроме того, эта функция будет автоматически активироваться для новых семейств сайтов.|  
|**Компонент интеграции сервера отчетов**|Позволяет использовать расширенные возможности создания отчетов с помощью служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<br /><br /> Этот компонент активен по умолчанию.|  
|**Компонент интеграции Power View**|Включает интерактивное исследование данных и визуальное представление для книг [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и табличных баз данных служб Analsysis Services.<br /><br /> Доступ к этому компоненту можно получить через контекстное меню следующих источников данных:<br /><br /> **RDLX;**<br /><br /> **RSDS**<br /><br /> файл соединения с**BISM** .<br /><br /> <br /><br /> Если [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] отсутствует в контекстном меню, убедитесь, что **интеграция Power View** включена.<br /><br /> По умолчанию эта функция отключена.|  
  
## См. также  
 [Активация функций интеграции семейства веб-сайтов с сервером отчетов и Power View в SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Страницы "Параметры сайта" и "Возможности сайта" служб Reporting Services (режим интеграции с SharePoint)](../../reporting-services/report-server-sharepoint/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  
  
  