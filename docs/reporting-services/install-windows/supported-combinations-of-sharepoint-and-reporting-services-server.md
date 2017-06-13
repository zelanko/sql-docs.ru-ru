---
title: "Поддерживаемые сочетания SharePoint и сервер служб Reporting Services | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 10/07/2016
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2e66cac836de44e8d2a9f23d88a600daaa26c0d1
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="supported-combinations-of-sharepoint-and-reporting-services-server"></a>Поддерживаемые сочетания SharePoint и сервером служб Reporting Services
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

  Серверу отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , установленному в режиме интеграции с SharePoint, требуется версия SharePoint и надстройка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (rsSharePoint.msi) для продуктов SharePoint, установленных на серверах SharePoint.  В этом разделе описаны поддерживаемые сочетания.  
  
## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>Поддерживаемые сочетания SharePoint и компонентов служб Reporting Services  
 В следующей таблице представлены поддерживаемые сочетания сервера отчетов, надстройки служб Reporting Services для продуктов SharePoint и продуктов SharePoint. Сочетания, отсутствующие в следующей таблице, не поддерживаются  
  
### <a name="supported-combinations"></a>Поддерживаемые сочетания  
  
||Сервер отчетов|Надстройка|Версия SharePoint|  
|-|-------------------|-------------|------------------------|  
|1|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|SharePoint 2016|  
|2|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|SharePoint 2013|  
|3|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2013|  
|4|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|  
|5|SQL Server 2012 с пакетом обновления 3 (SP3)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и SQL Server 2012 с пакетом обновления 3 (SP3)|SharePoint 2013|  
|6|SQL Server 2012 с пакетом обновления 2 (SP2)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и SQL Server 2012 с пакетом обновления 2 (SP2)|SharePoint 2013|  
|7|[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и средой [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2013|  
|8|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и средой [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]*|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|  
|9|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|SharePoint 2010|  
|10|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|  
|11|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и средой [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2010|  
|12|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|SharePoint 2010|  
|13|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с пакетом обновления 2 (SP2)|SharePoint 2007|  
|14|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с пакетом обновления 2 (SP2)|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] R2|SharePoint 2010|  
|15|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с пакетом обновления 2 (SP2)|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с пакетом обновления 2 (SP2)|SharePoint 2007|  
  
 *Исключение: интеграция с Power View не поддерживается.  
  
 Ссылки на страницы загрузки см. в статье [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
 **Дополнительные замечания**  

- Установите обновление, чтобы обновить все серверы SharePoint в пределах фермы. Сюда входят серверы приложений и веб-интерфейса.

-   Для поддержки SharePoint 2016, включая интеграцию с Power View, требуется сервер отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и надстройка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 2016 или более поздней версии.  

-   Для поддержки SharePoint 2013, включая интеграцию с Power View, требуется сервер отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и надстройка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 2012 SP1 или более поздней версии.  
  
-   Power View был впервые введен в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Таким образом, для интеграции Power View с SharePoint 2010 требуется версия надстройки [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или более поздняя.  
  
-   Надстройка служб SQL Server 2008 R2 не поддерживается сервером отчетов SQL Server 2012 (или более поздних версий). Программа установки компонентов, необходимых для SharePoint 2010, автоматически устанавливает надстройку служб SQL Server 2008 R2. Ее необходимо удалить перед установкой более новых версий надстройки. Обновление надстройки на месте не поддерживается.  
  
-   **Обновление.** SharePoint 2010 с установленной надстройкой [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] нельзя обновить на месте до SharePoint 2013. Для SharePoint 2013 требуется надстройка [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или более поздней и сервер отчетов. Дополнительные сведения по обновлению см. в разделе [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Возможности, поддерживаемые различными выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)   
 [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
  


