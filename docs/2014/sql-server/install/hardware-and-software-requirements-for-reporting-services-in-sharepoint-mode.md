---
title: Требования к оборудованию и программному обеспечению для Reporting Services в режиме интеграции с SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ed91877d-4f74-4266-a932-b824b4810c99
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c1f95544de8f0362b8981a175f1c65de1798a1eb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059320"
---
# <a name="hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode"></a>Требования к оборудованию и программному обеспечению для служб Reporting Services в режиме интеграции с SharePoint

  В этом разделе описываются необходимые условия, требования к оборудованию и рекомендации по установке для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] работы в режиме интеграции с SharePoint. Поскольку для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint требуется сервер SharePoint, большинство требований основаны на среде SharePoint. Для серверов отчетов, работающих в собственном режиме, оборудование должно соответствовать минимальным требованиям для работы [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   [Предварительные требования](#bkmk_prereq)  
  
-   [Требования к базе данных сервера отчетов](#bkmk_report_server_database)  
  
-   [Требования Power View](#bkmk_powerview)  
  
-   [Дополнительные сведения](#bkmk_more_information)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> Предварительные требования  
  
-   Для локальных установок учетная запись, в которую был выполнен вход при установке SharePoint, и службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] должны быть членами группы администраторов локальной операционной системы. Учетной записи установки не обязательно быть членом группы администраторов фермы SharePoint.  
  
     Дополнительные сведения см. в разделе [Разрешения и параметры безопасности учетной записи в SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx).  
  
-   Для работы служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции SharePoint требуется сервер SharePoint. Дополнительные сведения о требованиях и конфигурациях SharePoint см. в следующих разделах:  
  
    -   [Требования к оборудованию и программному обеспечению (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256365) (https://go.microsoft.com/fwlink/p/?LinkId=256365)  
  
    -   [Управление размером и его изменение для SharePoint Server 2013](https://technet.microsoft.com/library/cc261700.aspx)  
  
    -   [Требования к программному обеспечению для бизнес-аналитики (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256367)  
  
    -   [Требования к оборудованию и программному обеспечению (сервер SharePoint 2010)](https://technet.microsoft.com/library/cc262485\(v=office.14\))  
  
    -   [Управление размером и его изменение для SharePoint Server 2010](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))  
  
-   Если требуется обновить существующую установку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], см. раздел [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
-   Проверьте, запущена ли служба **Администрирование SharePoint 2013** в диспетчере Windows Server.  
  
###  <a name="report-server-database-requirements"></a><a name="bkmk_report_server_database"></a>Требования к базе данных сервера отчетов  
  
-   Как службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , так и продукты и технологии SharePoint используют для хранения данных приложений реляционные базы данных SQL Server.  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] требуется экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] с соответствующим выпуском SQL Server. Дополнительные сведения о требованиях к программному и аппаратному обеспечению см. в разделе [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Продукты SharePoint могут использовать существующий экземпляр базы данных. Если экземпляр [!INCLUDE[ssDE](../../includes/ssde-md.md)] не установлен, программа установки продуктов SharePoint устанавливает SQL Server Express Edition для баз данных приложений SQL Server.  
  
-   Экземпляр сервера отчетов не может использовать для своей базы данных выпуск SQL Server Express Edition. Однако экземпляр SQL Server Express Edition, установленный продуктом SharePoint, может существовать параллельно с другими выпусками ядра СУБД.  
  
##  <a name="sscrescent-requirements"></a><a name="bkmk_powerview"></a>[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]Требования к

 Ознакомьтесь с новейшей [документацией по Power View](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) на сайте Office.Microsoft.com. [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] входит в состав Microsoft Excel 2013 и является частью надстройки служб Reporting Services [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для выпусков Microsoft SharePoint Server 2010 и 2013 Enterprise.  
  
##  <a name="more-information"></a><a name="bkmk_more_information"></a> Дополнительные сведения

 Сведения об изменениях SharePoint см. в статье [изменения из sharepoint 2010 в sharepoint 2013](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) ( https://technet.microsoft.com/library/ff607742(office.15).aspx) .  
  
 [Заметки о Выпуске SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
  
