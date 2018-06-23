---
title: Устаревшие функции служб SQL Server Reporting Services в SQL Server 2014 | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
caps.latest.revision: 49
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: a52d82f4a2126c12dad3ec19cde3cc93ff22368d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190701"
---
# <a name="deprecated-features-in-sql-server-reporting-services-in-sql-server-2014"></a>Устаревшие функции служб SQL Server Reporting Services в SQL Server 2014
  В этом разделе описываются устаревшие функции служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Эти функции по-прежнему доступны в выпуске, где они признаны устаревшими, однако запланировано их удаление в следующем выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не следует использовать устаревшие функции в новых приложениях.  
  
 В этом разделе:  
  
-   [Устаревшие функции служб SQL Server 2014 Reporting Services](#bkmk_2014)  
  
-   [Устаревшие функции служб SQL Server 2012 SP1 Reporting Services](#bkmk_2012sp1)  
  
-   [Устаревшие функции служб SQL Server 2012 Reporting Services](#bkmk_2012)  
  
-   [Устаревшие функции служб SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="bkmk_2014"></a> Устаревшие функции служб SQL Server 2014 Reporting Services  
  
### <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Функции, не поддерживаемые в следующей версии SQL Server  
 Следующие [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] функции не будут поддерживаться в **Далее** версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не используйте их при работе над новыми приложениями и как можно скорее измените приложения, в которых они в настоящее время используются.  
  
#### <a name="html-rendering-extension-device-information-settings"></a>Параметры сведений об устройстве для модуля подготовки отчетов в формате HTML  
 Следующие параметры сведений об устройстве для модуля подготовки отчетов в формате HTML являются устаревшими.  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   Масштаб  
  
 Дополнительные сведения о модуле подготовки отчетов HTML см. в разделе [настройки сведений об устройстве HTML](html-device-information-settings.md)  
  
#### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Подготовка отчетов в формате Microsoft Word и Microsoft Excel 1997-2003  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Модули подготовки отчетов BIFF8 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отчеты в [!INCLUDE[msCoName](../includes/msconame-md.md)] Word и [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 формате BIFF. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] включает расширения, которые обрабатывают отчеты в [!INCLUDE[msCoName](../includes/msconame-md.md)] формате Open XML Office 2007-2010.  
  
#### <a name="report-definition-language-rdl-2005-and-earlier"></a>Язык определения отчетов 2005 и более ранних версий  
 Язык определения отчетов 2005 и более ранних версий считается устаревшим. Дополнительные сведения о языке RDL см. в разделе [языка определения отчетов &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).  
  
 Дополнительные сведения об обновлении отчетов см. в разделе [Upgrade Reports](install-windows/upgrade-reports.md).  
  
#### <a name="sql-server-2005-and-earlier-custom-report-items"></a>Пользовательские элементы отчета SQL Server 2005 и более ранних версий  
 Пользовательские элементы (ОТЧЕТА) компиляции для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 и более ранних версиях являются устаревшими.  
  
#### <a name="reporting-services-snapshots-2005-and-earlier"></a>Моментальные снимки служб Reporting Services 2005 и более ранних версий  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] подготовленные к просмотру с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 и более ранних версиях являются устаревшими.  
  
#### <a name="report-models"></a>Модели отчетов  
 Модели отчетов на языке семантического моделирования (SMDL) больше не поддерживаются. Хотя вы можете продолжать использовать модели отчетов в качестве источников данных [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] сообщает, следует рассмотреть возможность обновления отчетов, чтобы избавить их от зависимости от моделей отчетов.  
  
 Службы [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] больше не содержат средств для создания и изменения моделей отчетов. Дополнительные сведения см. в разделе [критические изменения в SQL Server Reporting Services в SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
#### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Устаревшие методы в конечной точке веб-службы  
 Следующие операции являются устаревшими в <xref:ReportService2010.ReportingService2010> конечной веб-службы:  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
#### <a name="sharepoint-web-parts"></a>Веб-части SharePoint  
 Установочный CAB-файл **RSWebParts.cab** и веб-части SharePoint, которые можно извлечь из него, являются устаревшими. Устаревшими веб-компонентами являются обозреватель отчетов (**SPExplorer.dwp**) и средство просмотра отчетов (**SPViewer.dwp**).  
  
 Дополнительные сведения об устаревших веб-частях см. в разделе [представление и просматривать собственного режима отчеты с помощью SharePoint Web частей (SSRS)](http://msdn.microsoft.com/library/ms159772.aspx)  
  
### <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Функции, не поддерживаемые в будущей версии SQL Server  
 Поддержка приведенных ниже функций компонента [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в следующей версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]будет сохранена, однако будет удалена в более поздней версии. (с какой именно версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , пока не определено).  
  
 Не [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отсутствуют устаревшие функции [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
##  <a name="bkmk_2012sp1"></a> Устаревшие функции служб SQL Server 2012 SP1 Reporting Services  
 В этом разделе описываются [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] устаревшие функции [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]. Поддержка приведенных ниже функций компонента [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в следующей версии [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]будет сохранена, однако будет удалена в более поздней версии. (с какой именно версии [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , пока не определено).  
  
### <a name="sharepoint-web-parts"></a>Веб-части SharePoint  
 Установочный CAB-файл **RSWebParts.cab** и веб-части SharePoint, которые можно извлечь из него, являются устаревшими. Устаревшими веб-компонентами являются обозреватель отчетов (**SPExplorer.dwp**) и средство просмотра отчетов (**SPViewer.dwp**).  
  
 Дополнительные сведения об устаревших веб-частях см. в разделе [представление и просматривать собственного режима отчеты с помощью SharePoint Web частей (SSRS)](http://msdn.microsoft.com/library/ms159772.aspx)  
  
##  <a name="bkmk_2012"></a> Устаревшие функции служб SQL Server 2012 Reporting Services  
 В этом разделе описываются [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] устаревшие функции [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
### <a name="html-rendering-extension-device-information-settings"></a>Параметры сведений об устройстве для модуля подготовки отчетов в формате HTML  
 Следующие параметры сведений об устройстве для модуля подготовки отчетов в формате HTML являются устаревшими.  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   Масштаб  
  
 Дополнительные сведения о модуле подготовки отчетов HTML см. в разделе [настройки сведений об устройстве HTML](html-device-information-settings.md)  
  
### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Подготовка отчетов в формате Microsoft Word и Microsoft Excel 1997-2003  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Модули подготовки отчетов BIFF8 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отчеты в [!INCLUDE[msCoName](../includes/msconame-md.md)] Word и [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 формате BIFF. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] включает расширения, которые обрабатывают отчеты в [!INCLUDE[msCoName](../includes/msconame-md.md)] формате Open XML Office 2007-2010.  
  
### <a name="report-definition-language-rdl-2005-and-earlier"></a>Язык определения отчетов 2005 и более ранних версий  
 Язык определения отчетов 2005 и более ранних версий считается устаревшим. Дополнительные сведения о языке RDL см. в разделе [языка определения отчетов &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).  
  
 Дополнительные сведения об обновлении отчетов см. в разделе [Upgrade Reports](install-windows/upgrade-reports.md).  
  
### <a name="sql-server-2005-and-earlier-custom-report-items"></a>Пользовательские элементы отчета SQL Server 2005 и более ранних версий  
 Пользовательские элементы (ОТЧЕТА) компиляции для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 и более ранних версиях являются устаревшими.  
  
### <a name="reporting-services-snapshots-2005-and-earlier"></a>Моментальные снимки служб Reporting Services 2005 и более ранних версий  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] подготовленные к просмотру с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 и более ранних версиях являются устаревшими.  
  
### <a name="report-models"></a>Модели отчетов  
 Модели отчетов на языке семантического моделирования (SMDL) больше не поддерживаются. Хотя вы можете продолжать использовать модели отчетов в качестве источников данных [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] сообщает, следует рассмотреть возможность обновления отчетов, чтобы избавить их от зависимости от моделей отчетов.  
  
 Службы [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] больше не содержат средств для создания и изменения моделей отчетов. Дополнительные сведения см. в разделе [критические изменения в SQL Server Reporting Services в SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Устаревшие методы в конечной точке веб-службы  
 Следующие операции являются устаревшими в <xref:ReportService2010.ReportingService2010> конечной веб-службы:  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
##  <a name="bkmk_kj"></a> Устаревшие функции служб SQL Server 2008 R2 Reporting Services  
  
> [!NOTE]  
>  Поскольку SQL Server 2008 R2 содержит изменения дополнительного номера версии по сравнению с SQL Server 2008, рекомендуется также просмотреть содержимое раздела по SQL Server 2008.  
  
### <a name="report-server-web-service-endpoints"></a>Конечные точки веб-службы сервера отчетов  
 Веб-службы <xref:ReportService2005.ReportingService2005> и <xref:ReportService2006.ReportingService2006> являются устаревшими в этом выпуске. Эти конечные точки были заменены новой конечной точки: <xref:ReportService2010.ReportingService2010>.  
  
 Новая конечная точка включает все функциональные возможности, доступные в устаревшей конечной точке, и новые средства, введенные в SQL Server 2008 R2.  
  
## <a name="see-also"></a>См. также  
 [Новые возможности &#40;службы Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Обратная совместимость](../getting-started/backward-compatibility.md)   
 [Изменения в SQL Server Reporting Services в SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Неподдерживаемые возможности в SQL Server Reporting Services в SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  