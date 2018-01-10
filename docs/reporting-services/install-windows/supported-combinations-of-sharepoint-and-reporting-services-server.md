---
title: "Поддерживаемые сочетания компонентов SharePoint и сервера служб Reporting Services | Документы Майкрософт"
ms.custom: 
ms.date: 07/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint mode
- add-in for sharepoint
- rsSharePoint
ms.assetid: dc6a3372-db26-43f0-b7aa-f725acc635c2
caps.latest.revision: "39"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 0446c7b50f78074e44258aa973f6cf970cb9f50a
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="supported-combinations-of-sharepoint-and-reporting-services-server"></a>Поддерживаемые сочетания компонентов SharePoint и сервера служб Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Серверу отчетов служб SQL Server Reporting Services, установленному в режиме интеграции с SharePoint, требуется версия SharePoint и надстройка служб SQL Server Reporting Services (rsSharePoint.msi) для продуктов SharePoint, установленных на серверах SharePoint. В этом разделе описаны поддерживаемые сочетания.

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.

## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>Поддерживаемые сочетания SharePoint и компонентов служб Reporting Services

 В следующей таблице представлены поддерживаемые сочетания сервера отчетов, надстройки служб Reporting Services для продуктов SharePoint и продуктов SharePoint. Сочетания, отсутствующие в следующей таблице, не поддерживаются

### <a name="supported-combinations"></a>Поддерживаемые сочетания

||Сервер отчетов|Надстройка|Версия SharePoint|
|-|-------------------|-------------|------------------------|
|1|SQL Server 2016|SQL Server 2016|SharePoint 2016|
|2|SQL Server 2016|SQL Server 2016|SharePoint 2013|
|3|SQL Server 2014|SQL Server 2014|SharePoint 2013|
|4|SQL Server 2014|SQL Server 2014|SharePoint 2010|
|5|SQL Server 2012 с пакетом обновления 3 (SP3)|SQL Server 2014 и SQL Server 2012 с пакетом обновления 3 (SP3)|SharePoint 2013|
|6|SQL Server 2012 с пакетом обновления 2 (SP2)|SQL Server 2014 и SQL Server 2012 с пакетом обновления 2 (SP2)|SharePoint 2013|
|7|SQL Server 2012 SP1|SQL Server 2014 и SQL Server 2012 с пакетом обновления 1 (SP1)|SharePoint 2013|
|8|SQL Server 2012 и SQL Server 2012 с пакетом обновления 1 (SP1)*|SQL Server 2014|SharePoint 2010|
|9|SQL Server 2012|SQL Server 2012|SharePoint 2010|
|10|SQL Server 2008 R2|SQL Server 2014|SharePoint 2010|
|11|SQL Server 2008 R2|SQL Server 2012 и SQL Server 2012 с пакетом обновления 1 (SP1) или более поздние версии|SharePoint 2010|
|12|SQL Server 2008 R2|SQL Server 2008 R2|SharePoint 2010|
|13|SQL Server 2008 R2|SQL Server 2008 с пакетом обновления 2 (SP2)|SharePoint 2007|
|14|SQL Server 2008 с пакетом обновления 2 (SP2)|SQL Server 2008 R2|SharePoint 2010|
|15|SQL Server 2008 с пакетом обновления 2 (SP2)|SQL Server 2008 и SQL Server 2008 с пакетом обновления 2 (SP2)|SharePoint 2007|

 *Исключение: интеграция с Power View не поддерживается.

 Ссылки на страницы загрузки см. в статье [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  

 **Дополнительные сведения:**

- Установите обновление, чтобы обновить все серверы SharePoint в пределах фермы. Сюда входят серверы приложений и веб-интерфейса.

- Для поддержки SharePoint 2016, включая интеграцию с Power View, требуется сервер отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и надстройка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 2016 или более поздней версии.

- Для поддержки SharePoint 2013, включая интеграцию с Power View, требуется сервер отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и надстройка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 2012 SP1 или более поздней версии.

- Power View появился в SQL Server 2012. Таким образом, для интеграции Power View с SharePoint 2010 требуется версия надстройки SQL Server 2012 или более поздняя.

- Надстройка служб SQL Server 2008 R2 не поддерживается сервером отчетов SQL Server 2012 (или более поздних версий). Программа установки компонентов, необходимых для SharePoint 2010, автоматически устанавливает надстройку служб SQL Server 2008 R2. Ее необходимо удалить перед установкой более новых версий надстройки. Обновление надстройки на месте не поддерживается.

- **Обновление.** SharePoint 2010 с установленной надстройкой [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] нельзя обновить на месте до SharePoint 2013. Для SharePoint 2013 требуется надстройка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] версии SQL Server 2012 с пакетом обновления 1 (SP1) или более поздней и сервер отчетов. Дополнительные сведения по обновлению см. в разделе [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).

## <a name="next-steps"></a>Следующие шаги

 [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Возможности, поддерживаемые различными выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)   
 [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
