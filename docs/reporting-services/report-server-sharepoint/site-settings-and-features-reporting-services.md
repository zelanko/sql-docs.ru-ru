---
title: "Параметры сайта и компоненты веб-сайтов (режим SharePoint) служб Reporting Services | Документы Microsoft"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0040fec-e2b7-4099-ae01-3b9bb9128bbd
caps.latest.revision: 10
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 044346bd4532c691861689662edbcbb37812b7ff
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="site-settings-and-features---reporting-services"></a>Параметры сайта и компонентов — службы Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint имеет несколько пользовательских компонентов уровня сайта, а также компонент сайта, которым можно управлять со страницы «Настройки сайта SharePoint». Эти параметры распространяются на весь сайт и влияют на все приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Для просмотра этой страницы требуются разрешения диспетчера содержимого или системного администратора.  
  
|Параметр сайта|Description|  
|------------------|-----------------|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Параметры сайта|Параметры для всего сайта, описанные в этом разделе.|  
|Управление оповещениями об изменении данных|Управление компонентом предупреждения об изменении данных.|  
|Синхронизация файлов сервера отчетов|Компонент уровня сайта, который по умолчанию отключен.<br /><br /> Синхронизирует файлы сервера отчетов (RDL, RSDS, SMDL, RSD, RSC, RDLX) между библиотекой документов SharePoint и сервером отчетов при добавлении или обновлении файлов непосредственно в библиотеке документов.<br /><br /> Дополнительные сведения см. в разделе [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md).|  
  
## <a name="to-open-the-reporting-services-site-settings-page"></a>Открытие страницы «Параметры сайта служб Reporting Services»  
  
1.  В меню **Действия сайта** сайта SharePoint выберите пункт **Параметры сайта**.  
  
2.  В разделе **Службы Reporting Services** выберите пункт **Параметры сайта служб Reporting Services**.  
  
## <a name="options-for-reporting-services-site-settings"></a>Параметры, приведенные на странице «Параметры сайта служб Reporting Services»  
  
|Параметр|Description|  
|------------|-----------------|  
|**Разрешить загрузку элемента управления RSClientPrint ActiveX**|Данный элемент управления отображает пользовательское диалоговое окно печати, в котором поддерживаются все стандартные функции: предварительный просмотр, указание отдельных страниц и их диапазонов, поля и ориентация страниц. Дополнительные сведения об этом элементе управления см. в разделе [Using the RSClientPrint Control in Custom Applications](../../reporting-services/report-server-web-service/net-framework/using-the-rsclientprint-control-in-custom-applications.md)|  
|**Разрешить отслеживание удаленных ошибок в локальном режиме**|Показывать или скрывать подробные сообщения об ошибках, возникающих на удаленных компьютерах при работе в локальном режиме. При появлении сообщения об ошибке, аналогичного приведенному далее, может оказаться полезным включение отслеживания удаленных ошибок.<br /><br /> `For more information about this error navigate to the report server on the local server machine or enable remote errors`|  
|**Включить метаданные о специальных возможностях для отчетов**|Включение метаданных о специальных возможностях в выходные данные HTML для отчетов|  
|**Включить точную подгонку визуализации данных под размер для отчетов**|Настройка точной подгонки визуализации данных при использовании внутри табликса. Сюда входят: диаграмма, датчик и карта. Когда этот параметр не установлен, визуализация данных подгоняется приблизительно, при этом может оставаться незанятое место. Этот параметр применяется только к отображению в веб-части средства просмотра отчетов. Для управления этим поведением при просмотре на стороне сервера необходимо изменить файл **rsreportserver.config** . Дополнительные сведения см. в следующих разделах:<br /><br /> [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).<br /><br /> [Customize Rendering Extension Parameters in RSReportServer.Config](../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md).<br /><br /> [HTML Device Information Settings](../../reporting-services/html-device-information-settings.md).<br /><br /> Включение этого параметра может негативно сказаться на производительности, поскольку на обработку для определения точного размера может уйти больше времени, чем при приблизительной подгонке.|  
  
## <a name="see-also"></a>См. также  
 [Управление Служебным приложением SharePoint службы Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)  
  
  
