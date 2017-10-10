---
title: "Поддерживаемые сочетания SharePoint и служб отчетов сервера | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint mode
- add-in for sharepoint
- rsSharePoint
ms.assetid: dc6a3372-db26-43f0-b7aa-f725acc635c2
caps.latest.revision: 39
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: b9fc7191c5ebb97cca0596b40e7db149d8293fd2
ms.contentlocale: ru-ru
ms.lasthandoff: 10/06/2017

---

# <a name="supported-combinations-of-sharepoint-and-reporting-services-server"></a>Поддерживаемые сочетания SharePoint и службы отчетов сервера

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Сервер отчетов служб SQL Server Reporting Services установлены в режиме интеграции с SharePoint требуется версия SharePoint и SQL Server Reporting Services надстройки (rsSharePoint.msi) для продуктов SharePoint, установленных на серверах SharePoint. В этом разделе описаны поддерживаемые сочетания.

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступны после SQL Server 2016.

## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>Поддерживаемые сочетания компонентов SharePoint и Reporting Services

 В следующей таблице представлены поддерживаемые сочетания сервера отчетов, надстройки служб Reporting Services для продуктов SharePoint и продуктов SharePoint. Сочетания, отсутствующие в следующей таблице, не поддерживаются

### <a name="supported-combinations"></a>Поддерживаемые сочетания

||Сервер отчетов|Надстройка|Версия SharePoint|
|-|-------------------|-------------|------------------------|
|1|SQL Server 2016|SQL Server 2016|SharePoint 2016|
|2|SQL Server 2016|SQL Server 2016|SharePoint 2013|
|3|SQL Server 2014|SQL Server 2014|SharePoint 2013|
|4|SQL Server 2014|SQL Server 2014|SharePoint 2010|
|5|SQL Server 2012 с пакетом обновления 3 (SP3)|SQL Server 2014 и SQL Server 2012 с пакетом обновления 3|SharePoint 2013|
|6|SQL Server 2012 с пакетом обновления 2 (SP2)|SQL Server 2014 и SQL Server 2012 SP2|SharePoint 2013|
|7|SQL Server 2012 SP1|SQL Server 2014 и SQL Server 2012 SP1|SharePoint 2013|
|8|SQL Server 2012 и SQL Server 2012 с пакетом обновления 1 *|SQL Server 2014|SharePoint 2010|
|9|SQL Server 2012|SQL Server 2012|SharePoint 2010|
|10|SQL Server 2008 R2|SQL Server 2014|SharePoint 2010|
|11|SQL Server 2008 R2|SQL Server 2012 и SQL Server 2012 SP1 или более поздней версии|SharePoint 2010|
|12|SQL Server 2008 R2|SQL Server 2008 R2|SharePoint 2010|
|13|SQL Server 2008 R2|SQL Server 2008 с пакетом обновления 2|SharePoint 2007|
|14|SQL Server 2008 с пакетом обновления 2|SQL Server 2008 R2|SharePoint 2010|
|15|SQL Server 2008 с пакетом обновления 2|SQL Server 2008 и SQL Server 2008 с пакетом обновления 2|SharePoint 2007|

 *Исключение: интеграция с Power View не поддерживается.

 Ссылки на страницы загрузки см. в статье [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  

 **Дополнительные вопросы:**

- Установите обновление, чтобы обновить все серверы SharePoint в пределах фермы. Сюда входят серверы приложений и веб-интерфейса.

- Для поддержки SharePoint 2016, включая интеграцию с Power View, требуется сервер отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и надстройка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 2016 или более поздней версии.

- Для поддержки SharePoint 2013, включая интеграцию с Power View, требуется сервер отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и надстройка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 2012 SP1 или более поздней версии.

- Power View был впервые введен в SQL Server 2012. Таким образом интеграции Power View в SharePoint 2010 требуется SQL Server 2012 или более поздней версии надстройки.

- Надстройка служб SQL Server 2008 R2 не поддерживается сервером отчетов SQL Server 2012 (или более поздних версий). Программа установки компонентов, необходимых для SharePoint 2010, автоматически устанавливает надстройку служб SQL Server 2008 R2. Ее необходимо удалить перед установкой более новых версий надстройки. Обновление надстройки на месте не поддерживается.

- **Обновление.** SharePoint 2010 с установленной надстройкой [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] нельзя обновить на месте до SharePoint 2013. SharePoint 2013 требуется SQL Server 2012 SP1 или более поздней [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] надстройки и сервера отчетов. Дополнительные сведения по обновлению см. в разделе [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).

## <a name="next-steps"></a>Следующие шаги

 [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Возможности, поддерживаемые различными выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)   
 [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
