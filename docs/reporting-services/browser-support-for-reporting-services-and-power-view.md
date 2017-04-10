---
title: "Поддержка браузера для служб Reporting Services и Power View | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "displaying reports"
  - "scripts [Reporting Services], requirements"
  - "viewing reports"
  - "browsers [Reporting Services]"
  - "Web browsers [Reporting Services], about browser support"
  - "browsing reports [Reporting Services]"
  - "components [Reporting Services], browsers"
  - "Web browsers [Reporting Services]"
ms.assetid: 48a75bbb-0029-4c43-891d-dc8f4fc0ebe1
caps.latest.revision: 121
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 121
---
# Поддержка браузера для служб Reporting Services и Power View
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

Вы можете узнать о том, какие версии браузера поддерживаются для просмотра [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], элементов управления ReportViewer и Power View и управления ими.
  
 **Область применения:** Основной режим [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] | Режим SharePoint для [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]  
  
##  <a name="bkmk_webportal"></a> Требования к браузеру для [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]

Далее приведен текущий список поддерживаемых браузеров для [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)].

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*
- Microsoft Edge (+)
- Microsoft Internet Explorer 10 или 11
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple iOS**  
*iPhone и iPad с iOS 9*

- Apple Safari (+)

**Google Android**  
*Смартфоны и планшетные ПК с Android 4.4 (KitKat) или более поздней версии*

- Google Chrome (+)

 **(+)** Последняя выпущенная версия  
  
##  <a name="bkmk_reportviewer"></a> Требования к браузеру для элемента управления ReportViewer (2015) 
 Далее приведен текущий список поддерживаемых браузеров для работы со средством просмотра отчетов (2015). Средство просмотра отчетов поддерживает просмотр отчетов с веб-портала [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и библиотек SharePoint.  
  
**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Edge (+)
- Microsoft Internet Explorer 10 или 11
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
  
 **(+)** Последняя выпущенная версия  
  
 При использовании продукта SharePoint, интегрированного со службами [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], ознакомьтесь с разделом [Планирование поддержки браузеров в SharePoint 2016](http://technet.microsoft.com//library/cc263526\(v=office.16\).aspx).  
  
###  <a name="bkmk_authentication"></a> Требования к проверке подлинности  
 Браузеры поддерживают определенные схемы проверки подлинности, обработка которых сервером отчетов является обязательным условием успешного выполнения клиентского запроса. В следующей таблице показаны типы проверки подлинности по умолчанию, поддерживаемые каждым браузером в операционной системе Windows.  
  
|**Тип браузера**|**Поддерживает**|**Выбор браузера по умолчанию**|**Выбор по умолчанию сервера**|  
|----------------------|------------------|-------------------------|------------------------|  
|**Microsoft Edge** (+)|Negotiate, Kerberos, NTLM, Basic|Согласование|Да. Используемые по умолчанию параметры проверки подлинности совместимы с Edge.|  
|**Microsoft Internet Explorer**|Negotiate, Kerberos, NTLM, Basic|Согласование|Да. Параметры проверки подлинности по умолчанию совместимы с Internet Explorer.|  
|**Google Chrome**(+)|Negotiate, NTLM, Basic|Согласование|Да. Параметры проверки подлинности по умолчанию совместимы с Chrome.|  
|**Mozilla Firefox**(+)|NTLM, базовый|NTLM|Да. Параметры проверки подлинности по умолчанию совместимы с Firefox.|  
|**Apple Safari**(+)|NTLM, базовый|Basic|Да. Параметры проверки подлинности по умолчанию совместимы с Safari.|  
  
 **(+)** Последняя выпущенная версия  
  
### Требования к скриптам для просмотра отчетов  
 Чтобы использовать средство просмотра отчетов, настройте браузер для выполнения скриптов.  
  
 Если поддержка скриптов отключена, появится сообщение об ошибке, похожее на следующее при открытии отчета:  
  
-   **Браузер не поддерживает выполнение скриптов, или выполнение скриптов запрещено в его настройках. Щелкните здесь для просмотра отчета без выполнения сценариев**.  
  
 При просмотре отчета без поддержки выполнения скриптов отчет готовится к просмотру в формате HTML без таких средств просмотра отчетов, как панель инструментов отчета и схема документа.  
  
> [!NOTE]  
>  Панель инструментов отчета является частью компонента «Средство просмотра HTML-страниц». По умолчанию панель инструментов появляется в верхней части каждого отчета, который отображается в окне браузера. C помощью средства просмотра отчета можно, в частности, выполнять поиск данных в отчете, прокручивать страницы и настраивать размер страниц для просмотра. Дополнительные сведения о панели инструментов отчета и средстве просмотра HTML-страниц см. в разделе [HTML Viewer and the Report Toolbar](../reporting-services/html-viewer-and-the-report-toolbar.md).  
  
##  <a name="bkmk_controls"></a> Поддержка браузеров для серверных веб-элементов управления ReportViewer в Visual Studio  
 Серверный веб-элемент управления ReportViewer используется для внедрения функций отчетов в веб-приложение ASP.NET. Эти элементы управления имеются в Visual Studio. Они могут поддерживать браузеры и версии браузеров, которые отличаются от браузеров и версий браузеров, поддерживаемых другими компонентами, описанными в этом разделе. Тип браузера, используемого для просмотра приложения, определяет то, какие функции ReportViewer могут быть реализованы в приложении. Используйте таблицу, приведенную в этом разделе, для определения того, какие из поддерживаемых браузеров имеют ограничения по функциям отчетов. В ней также указаны поддерживаемые платформы.  
  
 Используйте браузер, в котором включена поддержка скриптов. Если браузер не может выполнять скрипты, отчеты в нем просматривать нельзя.  
  
**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Edge (+)
- Microsoft Internet Explorer 10 или 11
- Google Chrome (+)
- Mozilla Firefox (+)
  
 **(+)** Последняя выпущенная версия  
  
##  <a name="bkmk_powerview"></a> Поддержка Power View в браузерах  

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Internet Explorer 10 или 11
- Mozilla Firefox (+)
  
**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
  
 **(+)** Последняя выпущенная версия  
  
 Дополнительные сведения о поддержке браузеров в SharePoint 2016 см. в разделе [Планирование поддержки браузеров в SharePoint 2013](http://technet.microsoft.com//library/cc263526\(v=office.16\).aspx).  
  
## См. также  
[Поиск и просмотр отчетов на веб-портале (построитель отчетов и службы SSRS)](http://msdn.microsoft.com/ru-ru/8556807e-f2e2-4a7b-bb1b-ac5ea1872e51)  
[Инструментальные средства служб Reporting Services](../reporting-services/tools/reporting-services-tools.md)  
[Веб-портал (основной режим служб SSRS)](http://msdn.microsoft.com/ru-ru/7349e626-6ed5-4d21-b05f-cf042ad9ad70)  
[Средство просмотра HTML-страниц и панель инструментов отчета](../reporting-services/html-viewer-and-the-report-toolbar.md)  
[Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md)  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]
