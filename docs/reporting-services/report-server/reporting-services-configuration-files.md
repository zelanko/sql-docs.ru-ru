---
title: Файлы конфигурации служб Reporting Services | Документы Майкрософт
ms.date: 05/30/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], configuration files
- configuration options [Reporting Services]
- modifying configuration files
- configuration files [Reporting Services]
ms.assetid: 21e5c32f-ad67-4917-b55a-8e21bd64f5a6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 25b695456bbac34e2c6ce8bf8c312c4108dd852e
ms.sourcegitcommit: 561cee96844b82ade6cf543a228028ad5c310768
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66506647"
---
# <a name="reporting-services-configuration-files"></a>Файлы конфигурации служб Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] хранят сведения о компонентах в реестре и файлах конфигурации, которые копируются в файловую систему при установке. Файлы конфигурации содержат комбинацию значений только для внутреннего использования и пользовательских значений. Пользовательские значения задаются при установке с помощью средств настройки, программ командной строки, а также посредством ручного редактирования файлов конфигурации.  
  
 Изменение файлов конфигурации необходимо только при добавлении или настройке дополнительных параметров. Параметры конфигурации задаются либо как элементы XML, либо как атрибуты. Если вы знакомы с XML и файлами конфигурации, то можете использовать редактор текста или кода для настройки пользовательских параметров. Дополнительные сведения об изменении файла конфигурации, а также о считывании сервером отчетов новых и обновленных параметров конфигурации см. в разделе [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
> [!NOTE]  
> В предыдущих версиях диспетчер отчетов имел собственный файл конфигурации с именем RSWebApplication.config. Этот файл устарел. Если выполняется обновление предыдущей установки, этот файл останется, но сервер отчетов не будет считывать из него параметры. Если файл RSWebApplication.config существует на компьютере, его следует удалить. В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях все параметры диспетчера отчетов хранятся в файле конфигурации RSReportServer.config и считываются из него. Список удаленных или перемещенных параметров см. в разделе [Критические изменения в службах SQL Server Reporting Services в выпуске SQL Server 2016](../../reporting-services/breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
 В этой статье  
  
-   [Сводка файлов конфигурации (собственный режим)](#bkmk_config_file_Summary_native_mode)  
  
-   [Сводка файлов конфигурации (режим интеграции с SharePoint)](#bkmk_config_file_Summary_sharepoint_mode)  
  
##  <a name="bkmk_config_file_Summary_native_mode"></a> Сводка файлов конфигурации (собственный режим)  
 В следующей таблице приводится описание мест хранения параметров настройки. Большая часть параметров настройки хранится в файлах конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. По умолчанию каталог установки следующий:  
  
''' Установка пути  
C:\Program Files\Microsoft SQL Server\MSRSxx.MSSQLSERVER, (где xx — номер версии MS SQL) или  
C:\Program Files\Microsoft SQL Server Reporting Services.  
  в зависимости от версии служб SSRS
```  
  
|Stored in:|Description|Location|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Stores configuration settings for feature areas of the Report Server service: Report Manager or the web portal, the Report Server Web service, and background processing. For more information about each setting, see [RsReportServer.config Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).|\<Installation directory> \Reporting Services \ReportServer|  
|RSSrvPolicy.config|Stores the code access security policies for the server extensions. For more information about this file, see [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Installation directory> \Reporting Services \ReportServer|  
|RSMgrPolicy.config|Stores the code access security policies for the web portal. For more information about this file, see [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Installation directory> \Reporting Services \ReportManager|  
|Web.config for the Report Server Web service|Includes only those settings that are required for ASP.NET.|\<Installation directory> \Reporting Services \ReportServer|  
|Web.config for Report Manager|Includes only those settings that are required for ASP.NET if applicable for the SSRS version.|\<Installation directory> \Reporting Services \ReportManager|  
|ReportingServicesService.exe.config|Stores configuration settings that specify the trace levels and logging options for the Report Server service. For more information about the elements in this file, see [ReportingServicesService Configuration File](../../reporting-services/report-server/reportingservicesservice-configuration-file.md).|\<Installation directory> \Reporting Services \ReportServer \Bin|  
|Registry settings|Stores configuration state and other settings used to uninstall Reporting Services. If you are troubleshooting an installation or configuration problem, you can view these settings to get information about how the report server is configured.<br /><br /> Do not modify these settings directly as this can invalidate your installation.|HKEY_LOCAL_MACHINE \SOFTWARE \Microsoft \Microsoft SQL Server \\<InstanceID\> \Setup<br /><br /> **- And -**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Services\ReportServer|  
|RSReportDesigner.config|Stores configuration settings for Report Designer. For more information, see [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md).|\<drive>:\Program Files \Microsoft Visual Studio 10 \Common7 \IDE \PrivateAssemblies.|  
|RSPreviewPolicy.config|Stores the code access security policies for the server extensions used during report preview. For more information about this file, see [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssembliesr|  
  
##  <a name="bkmk_config_file_Summary_sharepoint_mode"></a> Summary of configuration Files (SharePoint mode)  
 The following table provides a description of configuration files used for a SharePoint mode report server. Most configuration settings are stored in SharePoint service application databases. For more information, see [Reporting Services SharePoint Service and Service Applications](../../reporting-services/report-server-sharepoint/reporting-services-sharepoint-service-and-service-applications.md).  
  
 By default, the installation directory for SharePoint mode is the following:  
  
```Install path
C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting  
```  
  
|Место хранения|Описание|Местоположение|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Хранит параметры конфигурации для областей функций службы сервера отчетов: диспетчера отчетов, веб-службы сервера отчетов и фоновой обработки. Дополнительные сведения о каждом параметре см. в разделе [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).|\<каталог_установки>\Reporting Services\ReportServer|  
|RSSrvPolicy.config|Хранит политики управления доступом для кода для модулей сервера. Дополнительные сведения об этом файле см. в разделе [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<каталог_установки>\Reporting Services\ReportServer|  
|Файл Web.config для веб-службы сервера отчетов|Включает только те параметры, которые необходимы для ASP.NET, если это применимо для версии служб SSRS.|\<каталог_установки>\Reporting Services\ReportServer|  
|Параметры регистрации|Хранит состояние настройки и другие параметры, которые используются для отмены установки служб Reporting Services. Также хранит сведения о каждом приложении службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .<br /><br /> Не изменяйте эти параметры вручную, поскольку это может нарушить целостность установки.|HKEY_LOCAL_MACHINE \SOFTWARE \Microsoft \Microsoft SQL Server \\<ИД экземпляра\>\Setup<br /><br /> Идентификатор экземпляра образца: MSSQL13.MSSQLSERVER<br /><br /> **и**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Reporting Services\Service Applications|  
|RSReportDesigner.config|Хранит параметры настройки для конструктора отчетов. Дополнительные сведения см. в статье [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md).|\<диск>:\Program Files\Microsoft Visual Studio 10\Common7\IDE\PrivateAssemblies.|  
  
## <a name="see-also"></a>См. также раздел  
 [Сервер отчетов служб Reporting Services (основной режим)](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [модули служб Reporting Services](../../reporting-services/extensions/reporting-services-extensions.md)   
 [Программа rsconfig (SSRS)](../../reporting-services/tools/rsconfig-utility-ssrs.md)   
 [Запуск и остановка службы сервера отчетов](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  
