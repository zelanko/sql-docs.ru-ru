---
title: Файлы конфигурации служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], configuration files
- configuration options [Reporting Services]
- modifying configuration files
- configuration files [Reporting Services]
ms.assetid: 21e5c32f-ad67-4917-b55a-8e21bd64f5a6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 63d2dff214ed1125450ec319dff4ad7f7dc36990
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59939810"
---
# <a name="reporting-services-configuration-files"></a>Файлы конфигурации служб Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] хранят сведения о компонентах в реестре и файлах конфигурации, которые копируются в файловую систему при установке. Файлы конфигурации содержат комбинацию значений только для внутреннего использования и пользовательских значений. Пользовательские значения задаются при установке с помощью средств настройки, программ командной строки, а также посредством ручного редактирования файлов конфигурации.  
  
 Изменение файлов конфигурации необходимо только при добавлении или настройке дополнительных параметров. Параметры конфигурации задаются либо как элементы XML, либо как атрибуты. Если вы знакомы с XML и файлами конфигурации, то можете использовать редактор текста или кода для настройки пользовательских параметров. Дополнительные сведения об изменении файла конфигурации, а также о считывании сервером отчетов новых и обновленных параметров конфигурации см. в разделе [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
> [!NOTE]  
>  В предыдущих версиях диспетчер отчетов имел собственный файл конфигурации с именем RSWebApplication.config. Этот файл устарел. Если выполняется обновление предыдущей установки, этот файл останется, но сервер отчетов не будет считывать из него параметры. Если файл RSWebApplication.config существует на компьютере, его следует удалить. В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях все параметры диспетчера отчетов хранятся в файле конфигурации RSReportServer.config и считываются из него. Список, из которых были удалены или перемещенных параметров см. в разделе [критические изменения в SQL Server Reporting Services в SQL Server 2014](../breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
 В этом разделе:  
  
-   [Сводка файлов конфигурации (собственный режим)](#bkmk_config_file_Summary_native_mode)  
  
-   [Сводка файлов конфигурации (режим интеграции с SharePoint)](#bkmk_config_file_Summary_sharepoint_mode)  
  
##  <a name="bkmk_config_file_Summary_native_mode"></a> Сводка файлов конфигурации (собственный режим)  
 В следующей таблице приводится описание мест хранения параметров настройки. Большая часть параметров настройки хранится в файлах конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. По умолчанию каталог установки следующий:  
  
```  
C:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER  
```  
  
|Место хранения|Описание|Местоположение|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Хранит параметры конфигурации для областей функций службы сервера отчетов: Диспетчер отчетов, сервер веб-службы отчетов и фоновой обработки. Дополнительные сведения о каждом параметре см. в разделе [RSReportServer Configuration File](rsreportserver-config-configuration-file.md).|\<каталог_установки>\Reporting Services\ReportServer|  
|RSSrvPolicy.config|Хранит политики управления доступом для кода для модулей сервера. Дополнительные сведения об этом файле см. в разделе [Using Reporting Services Security Policy Files](../extensions/secure-development/using-reporting-services-security-policy-files.md).|\<каталог_установки>\Reporting Services\ReportServer|  
|Файл RSMgrPolicy.config|Хранит политики управления доступом для кода для диспетчера отчетов. Дополнительные сведения об этом файле см. в разделе [Using Reporting Services Security Policy Files](../extensions/secure-development/using-reporting-services-security-policy-files.md).|\<каталог_установки>\Reporting Services\ReportManager|  
|Файл Web.config для веб-службы сервера отчетов|Включает только те параметры, которые необходимы для ASP.NET.|\<каталог_установки>\Reporting Services\ReportServer|  
|Файл Web.config для диспетчера отчетов|Включает только те параметры, которые необходимы для ASP.NET.|\<каталог_установки>\Reporting Services\ReportManager|  
|ReportingServicesService.exe.config|Хранит параметры настройки, задающие уровни трассировки и параметры журнала для служб сервера отчетов. Дополнительные сведения об элементах этого файла см. в разделе [ReportingServicesService Configuration File](reportingservicesservice-configuration-file.md).|\<каталог_установки>\Reporting Services\ReportServer\Bin|  
|Параметры регистрации|Хранит состояние настройки и другие параметры, которые используются для отмены установки служб Reporting Services. При устранении неполадок установки или настройки, можно просмотреть эти параметры, чтобы получить представление о настройке сервера отчетов.<br /><br /> Не изменяйте эти параметры вручную, поскольку это может нарушить целостность установки.|HKEY_LOCAL_MACHINE \SOFTWARE \Microsoft \Microsoft SQL Server \\<ИД экземпляра\>\Setup<br /><br /> **и**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Services\ReportServer|  
|RSReportDesigner.config|Хранит параметры настройки для конструктора отчетов. Дополнительные сведения см. в статье [RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md).|\<диск>:\Program Files\Microsoft Visual Studio 10\Common7\IDE\PrivateAssemblies.|  
|RSPreviewPolicy.config|Хранит политики управления доступом для кода для модулей сервера, которые используются во время предварительного просмотра отчета. Дополнительные сведения об этом файле см. в разделе [Using Reporting Services Security Policy Files](../extensions/secure-development/using-reporting-services-security-policy-files.md).|C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssembliesr|  
  
##  <a name="bkmk_config_file_Summary_sharepoint_mode"></a> Сводка файлов конфигурации (режим интеграции с SharePoint)  
 Следующая таблица содержит описание файлов конфигурации, используемых для сервера отчетов в режиме интеграции с SharePoint. Большинство параметров конфигурации хранятся в базах данных приложения службы SharePoint. Дополнительные сведения см. в разделе [Служба SharePoint и приложения служб Reporting Services](../reporting-services-sharepoint-service-and-service-applications.md).  
  
 По умолчанию каталог установки для режима интеграции с SharePoint следующий:  
  
```  
C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting  
```  
  
|Место хранения|Описание|Местоположение|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Хранит параметры конфигурации для областей функций службы сервера отчетов: Диспетчер отчетов, сервер веб-службы отчетов и фоновой обработки. Дополнительные сведения о каждом параметре см. в разделе [RSReportServer Configuration File](rsreportserver-config-configuration-file.md).|\<каталог_установки>\Reporting Services\ReportServer|  
|RSSrvPolicy.config|Хранит политики управления доступом для кода для модулей сервера. Дополнительные сведения об этом файле см. в разделе [Using Reporting Services Security Policy Files](../extensions/secure-development/using-reporting-services-security-policy-files.md).|\<каталог_установки>\Reporting Services\ReportServer|  
|Файл Web.config для веб-службы сервера отчетов|Включает только те параметры, которые необходимы для ASP.NET.|\<каталог_установки>\Reporting Services\ReportServer|  
|Параметры регистрации|Хранит состояние настройки и другие параметры, которые используются для отмены установки служб Reporting Services. Также хранит сведения о каждом приложении службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .<br /><br /> Не изменяйте эти параметры вручную, поскольку это может нарушить целостность установки.|HKEY_LOCAL_MACHINE \SOFTWARE \Microsoft \Microsoft SQL Server \\<ИД экземпляра\>\Setup<br /><br /> Идентификатор экземпляра образца: MSSQL12.MSSQLSERVER<br /><br /> **и**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Reporting Services\Service Applications|  
|RSReportDesigner.config|Хранит параметры настройки для конструктора отчетов. Дополнительные сведения см. в статье [RSReportDesigner Configuration File](rsreportdesigner-configuration-file.md).|\<диск>:\Program Files\Microsoft Visual Studio 10\Common7\IDE\PrivateAssemblies.|  
  
## <a name="see-also"></a>См. также  
 [Сервер отчетов служб Reporting Services (основной режим)](reporting-services-report-server-native-mode.md)   
 [модули служб Reporting Services](../extensions/reporting-services-extensions.md)   
 [Программа rsconfig (SSRS)](../tools/rsconfig-utility-ssrs.md)   
 [Запуск и остановка службы сервера отчетов](start-and-stop-the-report-server-service.md)  
  
  
