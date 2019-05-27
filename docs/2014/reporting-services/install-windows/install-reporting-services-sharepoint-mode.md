---
title: Установку в режиме интеграции с SharePoint (SharePoint 2010 и SharePoint 2013) служб Reporting Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef049b4ded6408e651d5ec2c3db99c10bf7c27b6
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66108768"
---
# <a name="reporting-services-sharepoint-mode-installation-sharepoint-2010-and-sharepoint-2013"></a>Установка служб Reporting Services в режиме интеграции с SharePoint (SharePoint 2010 и SharePoint 2013)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в SharePoint режим является коллекцией из серверных компонентов, которые обеспечивают создание отчетов и доставку, на основе [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[msCoName](../../includes/msconame-md.md)] продуктов SharePoint.  
  
 Выполнение служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме SharePoint обеспечивает функции [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] и предупреждений об изменении данных. Дополнительные сведения о функциях в режиме интеграции с SharePoint, в подразделе «Поддержка функций и поведение различия в режимах сервера» раздела [сервер отчетов служб Reporting Services](../reporting-services-report-server.md)  
  
 Для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме SharePoint требуются две базовые установки.  
  
|Установка|Описание|  
|------------------|-----------------|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Надстройки для продуктов SharePoint.|Эта надстройка устанавливает страницы пользовательского интерфейса и компоненты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на сервер клиентского веб-интерфейса SharePoint. В компоненты пользовательского интерфейса входят [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], страницы в центре администрирования SharePoint, страницы компонентов, используемые в библиотеках документов SharePoint, и страницы предупреждений об изменении данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Сервера отчетов, установленного в режиме интеграции с SharePoint|Сервер отчетов обеспечивает обработку и подготовку данных и отчетов, а также обработку подписок и предупреждений об изменении данных. Сервер отчетов в режиме SharePoint формируется и устанавливается в виде общей службы SharePoint.|  
  
 Для установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] используется установочный носитель [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Инструкции по расширенным вариантам развертывания см. в разделе [контрольный список развертывания: Службы Reporting Services, Power View и PowerPivot для SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) и [контрольный список развертывания: Установка служб Reporting Services в существующей ферме SharePoint](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Поддерживаемые сочетания SharePoint и компонентов служб Reporting Services и надстройки &#40;SQL Server 2014&#41;](supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [Установка Reporting Services в режиме SharePoint для SharePoint 2013](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
 [Установка служб Reporting Services в режиме SharePoint для SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 [Установка или удаление Reporting Services надстройки для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [Где найти надстройку службы Reporting Services для продуктов SharePoint](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [Добавление дополнительного сервера отчетов в ферму (горизонтально масштабируемые службы SSRS)](add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [Добавление дополнительного клиентского веб-интерфейса служб Reporting Services в ферме](add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Настройка электронной почты для приложения служб Reporting Services (SharePoint 2010 и SharePoint 2013)](configure-e-mail-for-a-reporting-services-service-application.md)  
  
 [Подготовка подписок и предупреждений для приложений служб SSRS](provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Служба claims to Windows Token Service &#40;C2WTS&#41; и службы Reporting Services](../../sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a>См. также  
 [Архитектура предупреждений об изменении данных и рабочий процесс](../reporting-services-data-alerts.md#AlertingWF)   
 [Диспетчер предупреждений данных для оповещения администраторов](../data-alert-manager-for-alerting-administrators.md)  
  
  
