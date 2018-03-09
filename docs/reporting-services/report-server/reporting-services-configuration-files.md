---
title: "Файлы конфигурации служб Reporting Services | Документы Майкрософт"
ms.custom: 
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-server
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [Reporting Services], configuration files
- configuration options [Reporting Services]
- modifying configuration files
- configuration files [Reporting Services]
ms.assetid: 21e5c32f-ad67-4917-b55a-8e21bd64f5a6
caps.latest.revision: "52"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: d380872d275b3cea292b331978a49e9a17eae58c
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="reporting-services-configuration-files"></a>Файлы конфигурации служб Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] хранят сведения о компонентах в реестре и файлах конфигурации, которые копируются в файловую систему при установке. Файлы конфигурации содержат комбинацию значений только для внутреннего использования и пользовательских значений. Пользовательские значения задаются при установке с помощью средств настройки, программ командной строки, а также посредством ручного редактирования файлов конфигурации.  
  
 Изменение файлов конфигурации необходимо только при добавлении или настройке дополнительных параметров. Параметры конфигурации задаются либо как элементы XML, либо как атрибуты. Если вы знакомы с XML и файлами конфигурации, то можете использовать редактор текста или кода для настройки пользовательских параметров. Дополнительные сведения об изменении файла конфигурации, а также о считывании сервером отчетов новых и обновленных параметров конфигурации см. в разделе [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
> [!NOTE]  
>  В предыдущих версиях диспетчер отчетов имел собственный файл конфигурации с именем RSWebApplication.config. Этот файл устарел. Если выполняется обновление предыдущей установки, этот файл останется, но сервер отчетов не будет считывать из него параметры. Если файл RSWebApplication.config существует на компьютере, его следует удалить. В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях все параметры диспетчера отчетов хранятся в файле конфигурации RSReportServer.config и считываются из него. Список удаленных или перемещенных параметров см. в разделе [Критические изменения в службах SQL Server Reporting Services в выпуске SQL Server 2016](../../reporting-services/breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
 В этом разделе:  
  
-   [Сводка файлов конфигурации (собственный режим)](#bkmk_config_file_Summary_native_mode)  
  
-   [Сводка файлов конфигурации (режим интеграции с SharePoint)](#bkmk_config_file_Summary_sharepoint_mode)  
  
##  <a name="bkmk_config_file_Summary_native_mode"></a> Сводка файлов конфигурации (собственный режим)  
 В следующей таблице приводится описание мест хранения параметров настройки. Большая часть параметров настройки хранится в файлах конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. По умолчанию каталог установки следующий:  
  
```  
C:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER  
```  
  
|Место хранения|Description|Местоположение|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Хранит параметры конфигурации для областей функций службы сервера отчетов: диспетчера отчетов, веб-службы сервера отчетов и фоновой обработки. Дополнительные сведения о каждом параметре см. в разделе [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).|\<каталог_установки>\Reporting Services\ReportServer|  
|RSSrvPolicy.config|Хранит политики управления доступом для кода для модулей сервера. Дополнительные сведения об этом файле см. в разделе [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<каталог_установки>\Reporting Services\ReportServer|  
|Файл RSMgrPolicy.config|Хранит политики управления доступом для кода для диспетчера отчетов. Дополнительные сведения об этом файле см. в разделе [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<каталог_установки>\Reporting Services\ReportManager|  
|Файл Web.config для веб-службы сервера отчетов|Включает только те параметры, которые необходимы для ASP.NET.|\<каталог_установки>\Reporting Services\ReportServer|  
|Файл Web.config для диспетчера отчетов|Включает только те параметры, которые необходимы для ASP.NET.|\<каталог_установки>\Reporting Services\ReportManager|  
|ReportingServicesService.exe.config|Хранит параметры настройки, задающие уровни трассировки и параметры журнала для служб сервера отчетов. Дополнительные сведения об элементах этого файла см. в разделе [ReportingServicesService Configuration File](../../reporting-services/report-server/reportingservicesservice-configuration-file.md).|\<каталог_установки>\Reporting Services\ReportServer\Bin|  
|Параметры регистрации|Хранит состояние настройки и другие параметры, которые используются для отмены установки служб Reporting Services. При устранении неполадок установки или настройки, можно просмотреть эти параметры, чтобы получить представление о настройке сервера отчетов.<br /><br /> Не изменяйте эти параметры вручную, поскольку это может нарушить целостность установки.|HKEY_LOCAL_MACHINE \SOFTWARE \Microsoft \Microsoft SQL Server \\<ИД экземпляра\>\Setup<br /><br /> **и**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Services\ReportServer|  
|RSReportDesigner.config|Хранит параметры настройки для конструктора отчетов. Дополнительные сведения см. в статье [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md).|\<диск>:\Program Files\Microsoft Visual Studio 10\Common7\IDE\PrivateAssemblies.|  
|RSPreviewPolicy.config|Хранит политики управления доступом для кода для модулей сервера, которые используются во время предварительного просмотра отчета. Дополнительные сведения об этом файле см. в разделе [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssembliesr|  
  
##  <a name="bkmk_config_file_Summary_sharepoint_mode"></a> Сводка файлов конфигурации (режим интеграции с SharePoint)  
 Следующая таблица содержит описание файлов конфигурации, используемых для сервера отчетов в режиме интеграции с SharePoint. Большинство параметров конфигурации хранятся в базах данных приложения службы SharePoint. Дополнительные сведения см. в разделе [Служба SharePoint и приложения служб Reporting Services](../../reporting-services/report-server-sharepoint/reporting-services-sharepoint-service-and-service-applications.md).  
  
 По умолчанию каталог установки для режима интеграции с SharePoint следующий:  
  
```  
C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting  
```  
  
|Место хранения|Description|Местоположение|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Хранит параметры конфигурации для областей функций службы сервера отчетов: диспетчера отчетов, веб-службы сервера отчетов и фоновой обработки. Дополнительные сведения о каждом параметре см. в разделе [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).|\<каталог_установки>\Reporting Services\ReportServer|  
|RSSrvPolicy.config|Хранит политики управления доступом для кода для модулей сервера. Дополнительные сведения об этом файле см. в разделе [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<каталог_установки>\Reporting Services\ReportServer|  
|Файл Web.config для веб-службы сервера отчетов|Включает только те параметры, которые необходимы для ASP.NET.|\<каталог_установки>\Reporting Services\ReportServer|  
|Параметры регистрации|Хранит состояние настройки и другие параметры, которые используются для отмены установки служб Reporting Services. Также хранит сведения о каждом приложении службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .<br /><br /> Не изменяйте эти параметры вручную, поскольку это может нарушить целостность установки.|HKEY_LOCAL_MACHINE \SOFTWARE \Microsoft \Microsoft SQL Server \\<ИД экземпляра\>\Setup<br /><br /> Идентификатор экземпляра образца: MSSQL13.MSSQLSERVER<br /><br /> **и**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Reporting Services\Service Applications|  
|RSReportDesigner.config|Хранит параметры настройки для конструктора отчетов. Дополнительные сведения см. в статье [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md).|\<диск>:\Program Files\Microsoft Visual Studio 10\Common7\IDE\PrivateAssemblies.|  
  
## <a name="see-also"></a>См. также:  
 [Сервер отчетов служб Reporting Services (основной режим)](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Модули служб Reporting Services](../../reporting-services/extensions/reporting-services-extensions.md)   
 [Программа rsconfig (SSRS)](../../reporting-services/tools/rsconfig-utility-ssrs.md)   
 [Запуск и остановка службы сервера отчетов](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  
