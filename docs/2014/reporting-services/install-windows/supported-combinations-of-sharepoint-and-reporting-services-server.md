---
title: Поддерживаемые сочетания SharePoint и компонентов служб Reporting Services и надстроек (SQL Server 2014) | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SharePoint mode
- add-in for sharepoint
ms.assetid: dc6a3372-db26-43f0-b7aa-f725acc635c2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05f0997cb73a156e54b22ad280fa5d6eb0ec7d73
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66108649"
---
# <a name="supported-combinations-of-sharepoint-and-reporting-services-server-and-add-in-sql-server-2014"></a>Поддерживаемые сочетания SharePoint, компонентов служб Reporting Services и надстроек (SQL Server 2014)
  Сервер отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] может быть установлен в режиме интеграции с SharePoint и интегрирован с развертыванием SharePoint. Не все функции поддерживаются во всех сочетаниях сервера отчетов, надстройки служб Reporting Services для SharePoint и продуктов SharePoint. В этом разделе описаны поддерживаемые сочетания. В [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] интеграция обеспечивается следующим сочетанием.  
  
-   Версия сервера отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], настроенного для работы в режиме интеграции с SharePoint.  
  
-   Продукт SharePoint  
  
-   Надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint, установленная на серверах SharePoint.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010 &#124; SharePoint 2007|  
  
## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>Поддерживаемые сочетания SharePoint и компонентов служб Reporting Services  
 В следующей таблице представлены поддерживаемые сочетания сервера отчетов, надстройки служб Reporting Services для продуктов SharePoint и продуктов SharePoint. Сочетания, отсутствующие в следующей таблице, не поддерживаются  
  
### <a name="supported-combinations"></a>Поддерживаемые сочетания  
  
||Сервер отчетов|Надстройка|Версия SharePoint|Поддерживается|  
|-|-------------------|-------------|------------------------|---------------|  
|1|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2013|Да|  
|2|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|Да|  
|3|[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2013|Да|  
|4|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|Да<br /><br /> Исключение: Интеграция с Power view не поддерживается.|  
|5|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|SharePoint 2010|Да|  
|6|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|Да|  
|7|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2010|Да|  
|8|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|SharePoint 2010|Да|  
|9|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с пакетом обновления 2 (SP2)|SharePoint 2007|Да|  
|10|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с пакетом обновления 2 (SP2)|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] R2|SharePoint 2010|Да|  
|11|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с пакетом обновления 2 (SP2)|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с пакетом обновления 2 (SP2)|SharePoint 2007|Да|  
  
 Дополнительные сведения о [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] функции и режимах сервера отчетов, см. в разделе [сервер отчетов служб Reporting Services](../reporting-services-report-server.md).  
  
 **Дополнительные замечания**  
  
-   Для поддержки SharePoint 2013, включая интеграцию с Power View, требуется сервер отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и надстройка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 2012 SP1 или более поздней версии.  
  
-   Power View был впервые введен в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Таким образом, для интеграции Power View с SharePoint 2010 требуется версия надстройки [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или более поздняя.  
  
-   Надстройка служб SQL Server 2008 R2 не поддерживается сервером отчетов SQL Server 2012 (или более поздних версий). Программа установки компонентов, необходимых для SharePoint 2010, автоматически устанавливает надстройку служб SQL Server 2008 R2. Ее необходимо удалить перед установкой более новых версий надстройки. Обновление надстройки на месте не поддерживается.  
  
-   **Обновление:** SharePoint 2010 с помощью [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] надстройка установлена, нельзя обновить на месте до SharePoint 2013. Для SharePoint 2013 требуется надстройка [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или более поздней и сервер отчетов. Дополнительные сведения по обновлению см. в разделе [Upgrade and Migrate Reporting Services](upgrade-and-migrate-reporting-services.md).  
  
## <a name="see-also"></a>См. также  
 [Где найти надстройку службы Reporting Services для продуктов SharePoint](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Функции, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Обновление и перенос служб Reporting Services](upgrade-and-migrate-reporting-services.md)  
  
  
