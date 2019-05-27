---
title: Файлы и источники журналов служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
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
manager: kfile
ms.openlocfilehash: 2c0e935cc3d5264a1d2f5569b62db416d85b0427
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66103381"
---
# <a name="reporting-services-log-files-and-sources"></a>Файлы и источники журналов служб Reporting Services
  Сервер отчетов [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и среда сервера отчетов поддерживает различные назначения журналов для записи сведений об операциях и состоянии сервера. Существует два основных типа журналов: журнал выполнения и журнал трассировки. В журнал выполнения заносятся сведения о статистике выполнения отчетов, аудите, диагностике производительности и оптимизации. В журнал трассировки заносятся сведения о сообщениях об ошибках и общей диагностике.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в собственном режиме  
  
 Следующая таблица представляет ссылки на дополнительную информацию о каждом журнале, включая информацию о расположении журнала и о том, как просматривать его содержимое.  
  
|Журнал|Описание|  
|---------|-----------------|  
|[Журнал выполнения сервера отчетов и представление ExecutionLog3](report-server-executionlog-and-the-executionlog3-view.md)|Журнал выполнения — это представление SQL Server, хранящееся в базе данных сервера отчетов.<br /><br /> Журнал выполнения сервера отчетов содержит данные об отдельных отчетах, включая сведения о том, когда и кем был выполнен отчет, куда он был доставлен и какой формат использовался при подготовке к просмотру.|  
|Журнал трассировки служб SharePoint|Для серверов отчетов, работающих в SharePoint, журналы трассировки SharePoint содержат данные служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] . Также вы можете задать специфические данные [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] для единой службы ведения журнала в SharePoint. Дополнительные сведения см. в разделе [Включение событий служб Reporting Services для журнала трассировки SharePoint (ULS)](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)|  
|[Журнал трассировки службы сервера отчетов](report-server-service-trace-log.md)|Журналы трассировки служб содержат подробные сведения, которые используются для отладки приложения или изучения причин возникновения проблем или событий.<br /><br /> `C:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles`|  
|[Журнал HTTP-запросов сервера отчетов](report-server-http-log.md)|Файл журнала HTTP содержит по одной записи для каждого HTTP-запроса и ответа, обработанного веб-службой сервера отчетов и диспетчером отчетов.|  
|[Журнал приложений Windows](windows-application-log.md)|Журнал приложений Microsoft Windows содержит сведения о событиях сервера отчетов.|  
|Журналы производительности Windows|Журналы производительности Windows содержат данные о производительности сервера отчетов. Можно создавать собственные журналы производительности и выбирать счетчики, состояние которых отражается в журнале. Дополнительные сведения см. в разделе [Monitoring Report Server Performance](monitoring-report-server-performance.md).|  
|Файлы журналов установки|Файлы журналов также создаются при установке. Если во время установки произошли ошибки, появились предупреждения или другие сообщения, то, изучив файлы журналов, можно найти причину и устранить неполадки. Дополнительные сведения см. в разделе [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).|  
|журналы IIS|Файлы журналов, созданные службами Microsoft Internet Information Services (IIS). Дополнительные сведения можно найти в статье [Способы включения ведения журналов в службах Internet Information Services (IIS)](https://support.microsoft.com/kb/313437).|  
|Видео|Ознакомьтесь с коротким видео, демонстрирующим использование Microsoft Power Query для просмотра файлов журнала [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .<br /><br /> ![просмотреть видео о журналах Power Query и SSRS](../media/generic-video-thumbnail.png "просмотреть видео о журналах Power Query и SSRS")|  
  
## <a name="see-also"></a>См. также  
 [Сервер отчетов служб Reporting Services (основной режим)](reporting-services-report-server-native-mode.md)   
 [Справочник по ошибкам и событиям (службы Reporting Services)](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
