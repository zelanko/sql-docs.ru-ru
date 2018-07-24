---
title: Настройка и администрирование сервера отчетов (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-server-sharepoint
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 7959539dde52351bc9679b9b4629e2d1a4105562
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38049142"
---
# <a name="configuration-and-administration-of-a-sql-server-reporting-services-ssrs-report-server"></a>Настройка и администрирование сервера отчетов служб SQL Server Reporting Services (SSRS)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

SQL Server Reporting Services представляют собой серверную платформу для создания отчетов, которая предоставляет широкий спектр готовых к использованию средств и служб для создания и развертывания отчетов организации и управления ими, а также функции программирования, которые позволят расширить и настроить функциональность отчетов. Среду создания отчетов можно интегрировать с продуктами SharePoint, чтобы пользоваться всеми преимуществами среды совместной работы, которые обеспечивает сайт SharePoint.

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.

В следующих разделах можно ознакомиться с основными понятиями, сценариями развертывания, процедурами и прочими сведениями, относящимися к интеграции среды служб Reporting Services с продуктами или технологиями SharePoint.  
  
-   Параметры меню в библиотеке документов SharePoint  
  
    -   [Диспетчер предупреждений данных для пользователей SharePoint](../../reporting-services/data-alert-manager-for-sharepoint-users.md)  
  
    -   [Создание подписок для серверов отчетов, работающих в режиме интеграции с SharePoint, и управление этими подписками](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)  
  
    -   [Обновление учетных данных в источниках данных отчетов с сайта SharePoint](../../reporting-services/report-data/update-credentials-in-report-data-sources-from-a-sharepoint-site.md)  
  
    -   [Управление общими наборами данных](../../reporting-services/report-data/manage-shared-datasets.md)  
  
    -   [Настройка параметров опубликованного отчета (службы Reporting Services в режиме интеграции с SharePoint)](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)  
  
    -   [Установка параметров обработки (службы Reporting Services в режиме интеграции с SharePoint)](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
-   [Компоненты семейства веб-сайтов служб Reporting Services](../../reporting-services/report-server-sharepoint/site-collection-features-reporting-services.md)  
  
-   [Активация функций интеграции семейства веб-сайтов с сервером отчетов и Power View в SharePoint](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)  
  
-   [Страницы "Параметры сайта" и "Возможности сайта" служб Reporting Services (режим интеграции с SharePoint)](../../reporting-services/report-server-sharepoint/site-settings-and-features-reporting-services.md)  
  
-   [активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  
  
-   [Добавление типов содержимого служб Reporting Services в библиотеку SharePoint](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
-   [Отчеты, созданные в локальном режиме и Отчеты, созданные в подключенном режиме, в средстве просмотра отчетов &#40;службы Reporting Services в режиме интеграции с SharePoint&#41;](../../reporting-services/report-server-sharepoint/local-mode-vs-connected-mode-reports-in-the-report-viewer.md)  
  
-   [Загрузка документов в библиотеку SharePoint (службы Reporting Services в режиме SharePoint)](../../reporting-services/report-server-sharepoint/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)  
  
-   [Установка параметров обработки (службы Reporting Services в режиме интеграции с SharePoint)](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
 Дополнительные общие сведения о службах Reporting Services см. в разделе [Службы Reporting Services](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения о других компонентах, средствах и ресурсах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в [электронной документации по SQL Server](../../sql-server/sql-server-technical-documentation.md).  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
