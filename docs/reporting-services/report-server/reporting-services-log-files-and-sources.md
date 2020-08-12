---
title: Файлы и источники журналов служб Reporting Services | Документы Майкрософт
description: Сведения о журналах, которые серверы отчетов и среды сервера отчетов используют в Reporting Services для записи сведений о выполнении и трассировке.
ms.date: 05/10/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting [Reporting Services], log files
- logs [Reporting Services]
- logs [Reporting Services], about log files
- report servers [Reporting Services], log files
- report server log files
- files [Reporting Services], logs
ms.assetid: 80ef0acc-cbef-49d0-87e7-844e3ce19604
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1e9fad0dad3b5a5d90339403d2d596bb95bf0759
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84541456"
---
# <a name="reporting-services-log-files-and-sources"></a>Файлы и источники журналов служб Reporting Services
  На сервере отчетов и в среде сервера отчетов используются различные назначения журналов для записи сведений об операциях и состоянии сервера. Существует два основных типа журналов: журнал выполнения и журнал трассировки. В журнал выполнения заносятся сведения о статистике выполнения отчетов, аудите, диагностике производительности и оптимизации. В журнал трассировки заносятся сведения о сообщениях об ошибках и общей диагностике.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме  
  
 Следующая таблица представляет ссылки на дополнительную информацию о каждом журнале, включая информацию о расположении журнала и о том, как просматривать его содержимое.  
  
|Журнал|Описание|  
|---------|-----------------|  
|[Журнал выполнения сервера отчетов и представление ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)|Журнал выполнения — это представление SQL Server, хранящееся в базе данных сервера отчетов.<br /><br /> Журнал выполнения сервера отчетов содержит данные об отдельных отчетах, включая сведения о том, когда и кем был выполнен отчет, куда он был доставлен и какой формат использовался при подготовке к просмотру.|  
|Журнал трассировки служб SharePoint|Для серверов отчетов, работающих в SharePoint, журналы трассировки SharePoint содержат данные служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Также вы можете задать специфические данные [!INCLUDE[ssRS](../../includes/ssrs.md)] для единой службы ведения журнала в SharePoint. Дополнительные сведения см. в разделе [Включение событий служб Reporting Services для журнала трассировки SharePoint (ULS)](../../reporting-services/report-server/turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)|  
|[Журнал трассировки службы сервера отчетов](../../reporting-services/report-server/report-server-service-trace-log.md)|Журналы трассировки служб содержат подробные сведения, которые используются для отладки приложения или изучения причин возникновения проблем или событий. Файлы журнала трассировки имеют вид ReportServerService_\<timestamp>.log и находятся в следующей папке:<br /><br /> В SQL Server Reporting Services 2016 или более ранних версиях: `C:\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\LogFiles`<br /><br /> В SQL Server Reporting Services 2017: `C:\Program Files\Microsoft SQL Server Reporting Services\SSRS\LogFiles`|  
|[Журнал HTTP-запросов сервера отчетов](../../reporting-services/report-server/report-server-http-log.md)|Файл журнала HTTP содержит запись всех HTTP-запросов и ответов, обрабатываемых веб-службой сервера отчетов.|  
|[Журнал приложений Windows](../../reporting-services/report-server/windows-application-log.md)|Журнал приложений Microsoft Windows содержит сведения о событиях сервера отчетов.|  
|Журналы производительности Windows|Журналы производительности Windows содержат данные о производительности сервера отчетов. Можно создавать собственные журналы производительности и выбирать счетчики, состояние которых отражается в журнале. Дополнительные сведения см. в разделе [Наблюдение за производительностью сервера отчетов](../../reporting-services/report-server/monitoring-report-server-performance.md).|  
|Файлы журналов установки SQL Server|Файлы журналов также создаются при установке. Если во время установки произошли ошибки, появились предупреждения или другие сообщения, то, изучив файлы журналов, можно найти причину и устранить неполадки. Дополнительные сведения см. в разделе [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).|  
|Журналы IIS|Файлы журналов, созданные службами Microsoft Internet Information Services (IIS). См. дополнительные сведения о [включении ведения журналов в службах Internet Information Services (IIS)](https://support.microsoft.com/kb/313437) (https://support.microsoft.com/kb/313437).|  
  
## <a name="see-also"></a>См. также:  
 [Сервер отчетов служб Reporting Services (основной режим)](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Справочник по ошибкам и событиям (службы Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
