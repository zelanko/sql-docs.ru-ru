---
title: "Новые возможности в Reporting Services (SSRS) | Документы Microsoft"
ms.date: 07/02/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- what's new [Reporting Services]
- Reporting Services, what's new
- SQL Server Reporting Services, what's new
- SSRS, what's new
ms.assetid: bc909063-6b84-4b3a-80d2-e93fc04b4b9d
caps.latest.revision: 206
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 3a8ed8433d06f9f0250c42f6e5a190bc64e30235
ms.contentlocale: ru-ru
ms.lasthandoff: 07/03/2017

---

# Новые возможности служб SQL Server Reporting Services (SSRS)
<a id="whats-new-in-sql-server-reporting-services-ssrs" class="xliff"></a>

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../includes/ssrs-appliesto-not-pbirs.md)]

Дополнительные сведения о новых возможностях SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Охватывает основные функциональные аспекты и обновляется по мере выпуска новых элементов.
  
  Сведения о новых возможностях в других компонентах SQL Server см. в разделе [новые возможности SQL Server 2017 г.](../sql-server/what-s-new-in-sql-server-2017.md) или [новые возможности SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md).
  
 **Загрузка** ![download](../analysis-services/media/download.png "download")
 
- Чтобы загрузить техническую версию отчетов (январь 2017 г.) Power BI в службах SQL Server Reporting Services и выпуск Power BI Desktop (службы SQL Server Reporting Services), перейдите в **[Центр загрузки Майкрософт](https://go.microsoft.com/fwlink/?linkid=839351)**.
  
-   Чтобы скачать [!INCLUDE[ssSQL15](../includes/sssql15-md.md)], перейдите на сайт  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**.  
  
-   Есть учетная запись Azure?  Затем перейдите  **[здесь](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016sp1enterprisewindowsserver2016/)**  Чтобы запустить виртуальную машину с уже установленным SQL Server.  

 ![Примечание](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "Примечание") текущие заметки о выпуске в разделе [SQL Server 2016 Release Notes](../sql-server/sql-server-2016-release-notes.md) или [заметки о выпуске сервера отчетов Power BI](https://powerbi.microsoft.com/documentation/reportserver-release-notes/).

Сведения о сервере отчетов Power BI см. в разделе [приступить к работе с сервером отчетов Power BI](https://powerbi.microsoft.com/documentation/reportserver-get-started/).

## Поддержка DAX теперь в построитель отчетов и SQL Server Data Tools в конструкторе запросов
<a id="query-designer-support-for-dax-now-in-report-builder-and-sql-server-data-tools" class="xliff"></a>

В последних версиях построителя отчетов и SQL Server Data Tools — версия-кандидат, теперь можно создать собственные запросы DAX к поддерживаемые модели табличных данных SQL Server Analysis Services. Перетаскивание полей и имеется запрос DAX, созданный для вас, вместо написания собственного можно использовать конструктор запросов в обеих средах.  
 
Узнайте больше о [блога службы Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/2017/03/09/query-designer-support-for-dax-now-available-in-report-builder-and-sql-server-data-tools/).

* Загрузить [построителя отчетов SQL Server 2016](https://go.microsoft.com/fwlink/?LinkId=734968).
* Загрузить [SQL Server Data Tools — версия-кандидат](https://docs.microsoft.com/sql/ssdt/sql-server-data-tools-ssdt-release-candidate).

> **Примечание**: можно использовать только в конструкторе запросов для DAX с источников табличных данных SSAS, встроенные в SQL Server 2016 +.
 
## Что нового в SQL Server 2016
<a id="whats-new-in-sql-server-2016" class="xliff"></a>
  
### Службы Reporting Services: [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]
<a id="reporting-services-includessrswebportal-non-markdownincludesssrswebportal-non-markdown-mdmd" class="xliff"></a>  
 Доступен новый [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] . Это обновленный, современный портал, который содержит отчеты о ключевых показателях эффективности, мобильные отчеты, отчеты с разбиением на страницы, а также файлы Excel и Power BI Desktop. [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] заменяет диспетчер отчетов, который использовался в предыдущих версиях. Кроме того, [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] позволяет загрузить издатель мобильных отчетов и построитель отчетов, не прибегая к технологии ClickOnce.
 
 Для создания мобильных отчетов будет нужен [!INCLUDE[SS_MobileReptPub_Short](../includes/ss-mobilereptpub-short-md.md)].  
  
 Дополнительные сведения о [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]см. в статье [Веб-портал (основной режим служб SSRS)](../reporting-services/web-portal-ssrs-native-mode.md).  
  
 ![ssRSPortal](../reporting-services/media/ssrsportal.png "ssRSPortal")  
 
 #### Пользовательская фирменная символика на веб-портале [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]
<a id="custom-branding-for-the-includessrswebportal-non-markdownincludesssrswebportal-non-markdown-mdmd" class="xliff"></a> 
  С помощью пакета настройки фирменной символики можно настроить [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] , задав логотип и цвета организации.  
  
  Дополнительные сведения об индивидуальной фирменной символике см. в разделе [Фирменная символика на веб-портале](http://msdn.microsoft.com/en-us/6dac97f7-02a6-4711-81a3-e850a6b40bf1).
 
 #### Ключевые показатели эффективности (KPI) на веб-портале [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]
<a id="key-performance-indicators-kpi-in-the-includessrswebportal-non-markdownincludesssrswebportal-non-markdown-mdmd" class="xliff"></a> 

В [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] можно создавать ключевые показатели эффективности (KPI), соответствующие папке, в которой вы находитесь. При создании KPI можно выбрать поля набора данных и суммировать эти значения. Кроме того, можно выбрать данные для дополнительной детализации.
  
 ![ssrs-webportal-kpi](../reporting-services/media/ssrs-webportal-kpi.png)
 
 Дополнительные сведения см. в разделе [Работа с ключевыми показателями эффективности на веб-портале](http://msdn.microsoft.com/en-us/a28cf500-6d47-4268-a248-04837e7a09eb).
  
 
 ### Мобильные отчеты
<a id="mobile-reports" class="xliff"></a>
 
Мобильные отчеты в службах Reporting Services представляют собой специализированные отчеты, оптимизированные для широкого ряда форм-факторов и обеспечивающие оптимальную работу с данными на мобильных устройствах. Мобильные отчеты содержат различные визуализации, от диаграмм времени, категорий и сравнения до древовидных и пользовательских карт. Подключите мобильные отчеты к различным источникам данных, включая локальные многомерные и табличные данные служб SQL Server Analysis Services. Мобильные отчеты можно составлять в области конструктора, настраивая строки и столбцы сетки и используя гибкие элементы мобильных отчетов, которые масштабируются в соответствии с любым размером экрана. Мобильные отчеты можно сохранять на сервере служб Reporting Services, а затем просматривать в браузере или мобильном приложении Power BI на устройствах iPad, iPhone, Android и Windows 10.
  
#### Издатель мобильных отчетов
<a id="mobile-report-publisher" class="xliff"></a>  
 [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)] позволяет создавать и публиковать мобильные отчеты SQL Server на [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
 ![SS_MRP_LayoutTabSmall](../reporting-services/media/ss-mrp-layouttabsm.png "SS_MRP_LayoutTabSmall")  
  
 Дополнительные сведения см. в разделе [Создание мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md).  
  
#### Мобильные отчеты SQL Server, размещаемые в службах Reporting Services, доступны в приложении Power BI Mobile
<a id="sql-server-mobile-reports-hosted-in-reporting-services-available-in-power-bi-mobile-app" class="xliff"></a>  
 Приложение Power BI Mobile для iOS на iPad и iPhone сейчас может отображать мобильные отчеты SQL Server, которые находятся на вашем локальном сервере отчетов.  
  
 ![SS_MRP_iPad_HomeSm](../reporting-services/media/ss-mrp-ipad-homesm.png "SS_MRP_iPad_HomeSm")  
  
 По умолчанию без внесения изменений в конфигурацию установить соединение будет невозможно. Дополнительные сведения о том, как разрешить приложению Power BI Mobile устанавливать соединение с сервером отчетов, см. в разделе [Enable a report server for Power BI Mobile access](../reporting-services/report-server/enable-a-report-server-for-power-bi-mobile-access.md).
  
### Поддержка режима SharePoint и SharePoint 2016
<a id="support-of-sharepoint-mode-and-sharepoint-2016" class="xliff"></a>  
 Службы[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] поддерживают интеграцию с SharePoint 2013 и SharePoint 2016.
 
Дополнительные сведения см. в разделе:  
  
-   [Поддерживаемые сочетания SharePoint, компонентов служб Reporting Services и надстроек (SQL Server 2016)](../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
-   [Где найти надстройку службы Reporting Services для продуктов SharePoint](../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [Установка режима интеграции с SharePoint для служб Reporting Services](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)  

### Поддержка платформы Microsoft .NET Framework 4
<a id="microsoft-net-framework-4-support" class="xliff"></a>  
 Службы[!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] поддерживают текущие версии Microsoft .NET Framework 4. Сюда входят версии 4.0 и 4.5.1. Если никакая из версий .Net Framework 4.x не установлена, программа установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] установит платформу .NET 4.0 на этапе установки компонентов.  

### Усовершенствования в отчетах
<a id="report-improvements" class="xliff"></a>

**Механизм визуализации HTML 5** : новый механизм визуализации HTML5, ориентированный на современные "полнофункциональные" веб-стандарты и современные браузеры.  Новый механизм визуализации больше не зависит от режима Quirks, используемого в некоторых старых браузерах.
  
 Дополнительные сведения о поддержке браузеров см. в разделе [Поддержка браузера для служб Reporting Services и Power View](../reporting-services/browser-support-for-reporting-services-and-power-view.md).  

**Современные отчеты с разбиением на страницы:** новые, современные стили для диаграмм, датчиков, карт и других средств визуального представления данных позволяют создавать современные удобные отчеты с разбивкой на страницы.
  
**"Дерево" и "солнечные лучи" диаграмм:** Улучшайте отчеты с помощью плоского дерева ![ssrs_treemap_icon](../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon") и "солнечные лучи" ![ssrs_sunburst_icon](../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon") диаграммы, замечательные возможности для отображения иерархических данных. Дополнительные сведения см. в разделе [Tree Map and Sunburst Charts in Reporting Services](../reporting-services/report-design/tree-map-and-sunburst-charts-in-reporting-services.md).  

**Внедрение отчетов:** сегодня с помощью iframe, а также параметров URL-адреса мобильные отчеты и отчеты с разбиением по страницам можно внедрять в другие веб-страницы и приложения.  

**Закрепление элементов отчета на панели мониторинга Power BI** : при просмотре отчета в [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]можно выбрать элементы отчета и закрепить их на панели мониторинга [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] .   Закреплять можно такие элементы, как диаграммы, панели датчиков, карты и изображения. **(1)** Выберите группу, содержащую панель мониторинга, на которой нужно закрепить элемент; **(2)** выберите панель мониторинга, на которой требуется закрепить элемент; и **(3)** выберите частоту обновления плитки на этой панели мониторинга.   ![Примечание](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "Примечание") обновления управляется [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] подписки и после закрепления элемента можно изменить подписку и настроить другое расписание обновления.  
  
 ![ssRS_Pin_to_PowerBI](../reporting-services/media/ssrs-pin-to-powerbi.png) 
  
 Дополнительные сведения см. в разделах [Интеграция сервера отчетов с Power BI (диспетчер конфигурации)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md) и [Закрепление элементов служб Reporting Services на информационных панелях Power BI](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md).  
 
 **Визуализация в PowerPoint и экспорт**: новый модуль подготовки отчетов [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] имеет формат Microsoft PowerPoint (PPTX). Экспортировать отчеты в формате PPTX можно из обычных приложений, построителя отчетов, конструктора отчетов (в SSDT) и [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. Например, на следующем рисунке показано меню экспорта из [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. 
  
 ![ssrs-export-powerpoint](../reporting-services/media/ssrs-export-powerpoint.png) 
  
 Кроме того, формат PPTX можно выбрать для вывода подписок и использовать доступ по URL-адресу сервера отчетов для отрисовки и экспорта отчета. Например, следующая URL-команда в браузере экспортирует отчет из именованного экземпляра сервера отчетов.  
  
```  
http://servername/ReportServer_THESQLINSTANCE/Pages/ReportViewer.aspx?%2freportfolder%2freport+name+with+spaces&rs:Format=pptx  
```  
  
 Дополнительные сведения см. в разделе [Export a Report Using URL Access](../reporting-services/export-a-report-using-url-access.md).  
 
 **PDF заменяет ActiveX для удаленной печати** : функция печати ActiveX на панели инструментов в средстве просмотра отчетов была заменена современной функцией на основе PDF, которая работает в различных поддерживаемых браузерах, включая Microsoft Edge. Никаких дополнительных элементов управления ActiveX загружать не нужно! В зависимости от применяемого браузера, а также установленных приложений и служб просмотра PDF [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] либо будет открывать диалоговое окно для печати отчета, либо предлагать загрузить PDF-файл отчета.  При наличии прав администратора функцию печати на стороне клиента в [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]можно отключить. Дополнительные сведения см. в разделе [Включение и отключение печати на стороне клиента для служб Reporting Services](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md).

![ssrs-pdf-printing](../reporting-services/media/ssrs-pdf-printing.png)

### Усовершенствования подписки
<a id="subscription-improvements" class="xliff"></a>  
 
|Компонент|Поддерживаемый режим сервера|  
|-------------|---------------------------|  
|**Включение и отключение подписок**. Новые параметры пользовательского интерфейса для быстрого отключения и включения подписок. Отключенные подписки сохраняют другие свойства конфигурации, такие как расписание, и их можно легко включить.<br /><br /> ![ssrs-enable-disable-subscriptions](../reporting-services/media/ssrs-enable-disable-subscriptions.png)<br /><br /> Дополнительные сведения см. в разделе [Disable or Pause Report and Subscription Processing](../reporting-services/subscriptions/disable-or-pause-report-and-subscription-processing.md).|Основной режим|  
|**Описание подписки**. При создании новой подписки в свойства подписки теперь можно включить описание отчета. Описание добавляется на странице сводки о подписке.|SharePoint и собственный режим|  
|**Изменение владельца подписки**. Улучшенный пользовательский интерфейс для быстрого изменения владельца подписки. Предыдущие версии [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] позволяют администраторам изменять владельцев подписки с помощью скрипта. Начиная с версии [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] , владельца подписки можно изменять с помощью пользовательского интерфейса или скрипта. Изменение владельца подписки — это стандартная задача администрирования, выполняемая в случае увольнения пользователей или изменения их роли в организации.|SharePoint и собственный режим|  
|**Общие учетные данные для подписок на общую папку**. Благодаря подпискам на общую папку [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] сейчас существует два рабочих процесса.<br /><br /> Новая возможность в этой версии: администратор вашей [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] может настроить одну учетную запись для общей папки, которая будет использоваться для одной или нескольких подписок. Настройка учетной записи общей папки выполняется в диспетчере конфигурации собственного режима. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] **Укажите учетную запись общей папки**, а затем на странице конфигурации подписки установите флажок **Используется учетная запись общей папки**.<br /><br /> Настройка отдельных подписок с разными учетными данными для целевой общей папки.<br /><br /> Кроме того, два этих подхода можно использовать совместно. Например, когда какие-то подписки на общую папку используют централизованную учетную запись общей папки, а другие подписки используют разные учетные данные.|Основной режим|  

### SQL Server Data Tools (SSDT)
<a id="sql-server-data-tools-ssdt" class="xliff"></a>  
 Новая версия SSDT включает в себя шаблоны проектов для [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]: мастер проектов сервера отчетов и проект сервера отчетов. Сведения о загрузке SSDT см. в разделе [SQL Server Data Tools для Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkId=827542).  

### Усовершенствования построителя отчетов
<a id="report-builder-improvements" class="xliff"></a>

**Новый пользовательский интерфейс построителя отчетов** : пользовательский интерфейс в [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)] теперь имеет современный вид и содержит упрощенные элементы интерфейса.  
  
|||  
|-|-|  
|Создать|Previous|  
|![ssrs_rbfacelift_new](../reporting-services/media/ssrs-rbfacelift-new.png "ssrs_rbfacelift_new")|![ssrs_rbfacelift_old](../reporting-services/media/ssrs-rbfacelift-old.png "ssrs_rbfacelift_old")|  

**Панель пользовательских параметров** : сейчас можно настраивать панель параметров. С помощью области конструктора в построителе отчетов параметр можно перетащить в конкретный столбец и строку на панели параметров. Для изменения макета панели столбцы можно добавлять и удалять.   Дополнительные сведения см. в разделе [Настройка области параметров в отчете (построитель отчетов)](../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
 ![Список параметров в области данных отчета и в области параметров](../reporting-services/media/ssrs-customizeparameter-parameterlist-reportdatapane.png "список параметров в области данных отчета и в области параметров")  

  
**Поддержка высокого уровня Разрешения:** [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)] поддерживает масштабирование высокого DPI (точек на дюйм) и устройств.  Дополнительные сведения о высоком разрешении см. в следующих разделах:  
  
-   [Windows 8.1 DPI Scaling Enhancements](https://blogs.windows.com/windowsexperience/2013/07/15/windows-8-1-dpi-scaling-enhancements/)  
  
-   [Высокое разрешение и Windows 8.1](http://technet.microsoft.com/library/dn528848.aspx)  

## Следующие шаги
<a id="next-steps" class="xliff"></a>

[Новые возможности в службах Analysis Services](http://msdn.microsoft.com/en-us/aa69c299-b8f4-4969-86d8-b3292fe13f08)  
[Техническая версия отчетов Power BI в SSRS — заметки о выпуске](../reporting-services/reporting-services-release-notes.md)  
[Заметки о выпуске SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)   
[Обратная совместимость](http://msdn.microsoft.com/en-us/675b0e0e-cfee-4790-9675-80fc3ea6d30f)   
[Возможности служб Reporting Services, поддерживаемые различными выпусками SQL Server 2016](http://msdn.microsoft.com/en-us/39f03d2d-6e48-4b34-a9d3-07f86313b937)   
[Обновление и перенос служб Reporting Services](../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
[Службы Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
[Сервер отчетов бизнес-Аналитики Power](https://powerbi.microsoft.com/documentation/reportserver-get-started/)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
