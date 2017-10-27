---
title: "Reporting Services на сервере отчетов (режим SharePoint) | Документы Microsoft"
ms.custom: 
ms.date: 09/26/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: a8cd1bd00ec92535fff73c5eaa4ff9bbe9274ef2
ms.contentlocale: ru-ru
ms.lasthandoff: 10/06/2017

---

# <a name="reporting-services-report-server-sharepoint-mode"></a>Сервер отчетов служб Reporting Services (режим SharePoint)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  Сервер отчетов служб Reporting Services, настроенный для **режиме интеграции с SharePoint** можно запустить в составе развертывания продукта SharePoint. Сервер отчетов в режиме интеграции с SharePoint может использовать функции совместной работы и управления SharePoint для отчетов и других типов содержимого [!INCLUDE[ssRSnfoversion_md](../../includes/ssrsnoversion-md.md)] . Режиме интеграции с SharePoint требуется установить соответствующую версию надстройки служб Reporting Services для продуктов SharePoint на ваш веб-интерфейсом SharePoint.  
  
> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступны после SQL Server 2016.

 Дополнительные сведения об установке и настройке см. в следующем документе.  
  
-   [Установка режима интеграции с SharePoint служб Reporting Services для SharePoint 2010](http://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c).  
  
-   [Добавление дополнительного сервера отчетов в ферме](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).  
  
## <a name="feature-summary"></a>Сводка функций

 Настройка сервера отчетов для работы в режиме интеграции с SharePoint предоставляет следующие дополнительные возможности (доступные только при развертывании в этом режиме).  
  
-   Функции управления документами и совместной работы SharePoint, включая обработку предупреждений. Сайт SharePoint предоставляет единый портал для доступа ко всем документам и единую точку управления элементами отчета.  
  
-   Использование разрешений SharePoint и поставщиков служб проверки подлинности для управления доступом к отчетам, моделям и другим элементам.  
  
-   Топология развертывания SharePoint используется для распределения отчетов по Интернет-соединению за пределами брандмауэра. Сервер отчетов поддерживает службы обработки отчетов и данных в контексте более крупной конфигурации SharePoint, настроенной для доступа в Интернет.  
  
-   Управление отчетами, моделями, источниками данных, расписаниями и журналом отчетов с помощью пользовательских страниц приложений на сайте SharePoint. На сайте SharePoint можно задавать свойства, создавать расписания, оформлять подписки, а также создавать и вести журнал отчетов, используя те же методы, что и при работе с другими средствами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Публикация и передача отчетов, моделей отчетов, ресурсов и общих источников данных в библиотеку SharePoint, в том числе центр отчетов на сервере Office SharePoint.  
  
     Для создания отчетов и источников данных, которые будут публиковаться непосредственно в библиотеке SharePoint, используйте конструктор отчетов, конструктор моделей и построитель отчетов. Также можно использовать действие «Передача» на сайте SharePoint, чтобы добавить в библиотеку SharePoint любые определения отчетов и модели отчетов.  
  
     Сервер отчетов всегда обрабатывает определения отчетов одинаковым образом, независимо от используемого режима сервера, и режим сервера не влияет на данные отчета и его макет. Любой отчет, который может запускаться на сервере отчетов в собственном режиме, может запускаться и на сервере отчетов, настроенном для работы в режиме интеграции с SharePoint.  
  
-   Оформление подписки и доставка отчетов в библиотеку SharePoint с помощью нового модуля доставки SharePoint. Также можно доставлять отчеты по электронной почте или в общую папку. Для доставки отчетов применяются модули доставки сервера отчетов. Можно создать управляемые данными подписки для крупномасштабного распространения отчетов с использованием сведений о подписчике, запрошенных во время выполнения.  
  
-   Веб-части средства просмотра отчетов можно добавить на страницы SharePoint для просмотра отчетов в веб-приложении SharePoint. Веб-часть включает навигацию по страницам, поиск, печать и экспорт функций.  
  
-   Программирование в контексте новой конечной точки SOAP для создания пользовательских приложений, интегрируемых с сайтом SharePoint. Также можно использовать обновленный поставщик инструментария управления Windows (WMI) для программной настройки экземпляра сервера отчетов, работающего в режиме интеграции с SharePoint.  
  
-   Отчеты Microsoft Access в подключенном режиме.  
  
-   AAM-зоны, развертывания, направленные в сторону Интернета, и токены пользователя SharePoint для списков SharePoint.  
  
## <a name="connected-mode-and-local-mode"></a>Подключенный и локальный режимы

 В выпуске SQL Server 2008 R2 введен новый *локальный режим* для просмотра отчетов с сервера SharePoint 2010 с установленной надстройкой служб Microsoft SQL Server 2008 R2 Reporting Services (или более поздней версии) для продуктов SharePoint 2010.  
  
-   *Локальный режим*: локальный режим позволяет подготавливать локально из библиотеки документов SharePoint без интеграции с сервером отчетов служб Reporting Services отчеты. Надстройка служб Reporting Services для продуктов SharePoint является обязательным, но не является сервером отчетов Reporting Services. Надстройка может быть установлена несколькими различными способами, в том числе с помощью средства подготовки продуктов SharePoint 2010. Дополнительные сведения о локальном режиме см. в разделе [локальный режим и отчеты в подключенном режиме в средстве просмотра отчетов](../../reporting-services/report-server-sharepoint/local-mode-vs-connected-mode-reports-in-the-report-viewer.md) и [где найти надстройку служб Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
-   *Подключенный режим*: подключенный режим поддерживается путем интеграции сервера отчетов служб Reporting Services в ферме SharePoint, с помощью центра администрирования SharePoint. Интеграция с сервером отчетов обеспечивает комплексные возможности работы с отчетами, предоставляя функции совместной работы SharePoint 2010 и серверные функции сервера отчетов, в том числе подписку, моментальные снимки и серверную обработку.  
  
## <a name="unsupported-sharepoint-features"></a>Неподдерживаемые функции sharePoint

 При работе в режиме интеграции доступны не все компоненты SharePoint. Ниже приведен список функций SharePoint, службы Reporting Services не интегрируются напрямую.  
  
-   Служба Secure Store.  
  
-   Нельзя использовать интеграцию с календарем SharePoint Outlook и создавать расписания SharePoint для файлов служб отчетов в библиотеке документов.  
  
-   Каталог SharePoint Business Data.  
  
-   На страницах служб Reporting Services также не поддерживается возможность индивидуальной настройки SharePoint. Интеграция с сервером отчетов невозможна, если веб-приложение SharePoint включено для анонимного доступа.  
  
-   Службы SQL Server Reporting Services **не** поддерживают управление версиями библиотеки документов SharePoint. Если сохранить элементы отчета в библиотеке документов, для которой включена функция «История версий документов», то функции службы Reporting Services будут работать неправильно и в журнале ULS будут формироваться ошибки. В следующем примере показана ошибка в журнале ULS:  
  
    -   «...отключен источник данных, связанный с отчетом».  
  
     История версий документов библиотеки настраивается на странице «Параметры версий» окна «Настройки библиотеки».  
  
## <a name="supported-combinations-of-the-sharepoint-add-in-and-report-server"></a>Поддерживаемые сочетания SharePoint надстройки и сервера отчетов

 Не все функции поддерживаются во всех сочетаниях сервера отчетов, надстройки служб Reporting Services для SharePoint и продуктов SharePoint. Дополнительные сведения см. в разделе [поддерживаемые сочетания SharePoint и сервер служб Reporting Services и надстройки](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
> [!NOTE]  
>  Правильная версия надстройки служб Reporting Services должна использоваться с соответствующей версией продуктов SharePoint.  
  
## <a name="components-that-provide-integration"></a>Обеспечивающие интеграцию компоненты

 Для объединения серверов в одно развертывание, интегрировать установку служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служб Reporting Services с экземпляром продуктов SharePoint  
  
 Интеграция обеспечивается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и надстройки служб Reporting Services для продуктов SharePoint. Надстройка служб Reporting Services является свободно распространяемым компонентом, можно загрузить и затем установить на сервере, на котором работает с соответствующей версией SharePoint.  
  
> [!TIP]  
>  Не все функции поддерживаются во всех сочетаниях сервера отчетов, надстройки служб Reporting Services для SharePoint и продуктов SharePoint. Дополнительные сведения см. в разделе [поддерживаемые сочетания SharePoint и сервер служб Reporting Services и надстройки](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md).  
  
-   На сайте SharePoint надстройку служб Reporting Services предоставляет конечную точку прокси ReportServer, веб-части средства просмотра отчетов и страницы приложений, чтобы просматривать, хранить и управлять содержимым сервера отчетов на сайте SharePoint или ферме SharePoint.  
  
-   В службах Reporting Services предоставляет обновленные файлы программ, конечную точку SOAP и пользовательские модули безопасности и доставки. Сервер отчетов должен быть настроен для работы в режиме интеграции с SharePoint, специально выделенном для поддержки доступа к отчетам и их доставки через сайт SharePoint.  
  
 После установки надстройки служб Reporting Services в SharePoint и настройки двух серверов для интеграции, можно передать или опубликовать типы содержимого сервера отчетов в библиотеку SharePoint и затем просматривать и управлять этими документами с сайта SharePoint. Передача или публикация содержимого сервера отчетов является важным первым шагом. веб-части и страницы становятся доступны при выборе определений отчетов (RDL-файл), моделей отчетов (SMDL) и общих источников данных (RSDS-файл) на сайте SharePoint.  
  
##  <a name="language-considerations"></a>Дополнительные сведения

 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] и [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] поддерживают гораздо больше языков, чем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Если настроить сервер отчетов для работы с развертыванием продукта SharePoint, можно получить сочетание языков. Далее описано, какой язык будут иметь пользовательский интерфейс, документация и сообщения.  
  
-   Все страницы приложений, средства, ошибок, предупреждений и сообщений, поступающих от служб Reporting Services будет отображаться на языке, используемом экземпляром служб Reporting Services в одной из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] языков.  
  
-   Страницы приложений, открываемые на сайте SharePoint, веб-части средства просмотра отчетов и построителя отчетов будут отображаться в одном из языков, поддерживаемых для надстройки служб Reporting Services. Чтобы просмотреть список поддерживаемых языков, перейдите в [загрузки SQL Server](http://msdn.microsoft.com/sql/downloads/) и на странице загрузки для SQL Server 2016 Reporting Services надстройки.  
  
-   Сайты и центр администрирования SharePoint, справка в Интернете и сообщения доступны на языках, поддерживаемых продуктами Office Server.  
  
 Если язык вашего продукта или технологии SharePoint, отличается от языка сервера отчетов, службы Reporting Services будет пытаться использовать язык из той же языковой группы, который предоставляет наиболее точное соответствие. Если подходящий язык недоступен, сервер отчетов будет использовать английский язык.  
  
## <a name="related-tasks"></a>Связанные задачи

 В следующей таблице перечислены задачи, связанные с сервера отчетов в режиме Reporting Services SharePoint:  
  
|**Задача**|**Ссылка**|  
|--------------|--------------|  
|Подробные инструкции по установке и настройке служб Reporting Services в режиме интеграции с SharePoint.|[Установка режима интеграции с SharePoint служб Reporting Services для SharePoint 2010](http://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c) и [Добавление дополнительного сервера отчетов в ферме](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).|  
|Масштабное развертывание Reporting Services SharePoint путем добавления дополнительных серверов отчетов.|[Добавление дополнительного сервера отчетов в ферме](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) и [топологии развертывания для компонентов бизнес-Аналитики SQL Server в SharePoint](http://msdn.microsoft.com/library/39f76bc7-94e6-4dbc-bfa5-d56f4430bb26).|  
|Добавьте дополнительные SharePoint веб-интерфейсов, имеющих все компоненты служб Reporting Services для просмотра отчетов и элементов.|[Добавление дополнительных служб Reporting Services клиентского веб-интерфейса в ферме](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)|  
|Настройка электронной почты сервера отчетов в среде SharePoint.|[Настройка электронной почты для приложения службы Reporting Services](../install-windows/configure-e-mail-for-a-reporting-services-service-application.md)|
|Последние сведения об этом выпуске доступны на TechNet Wiki.|[SQL Server 2012 Reporting Services советы, рекомендации и устранение неполадок](http://go.microsoft.com/fwlink/?LinkId=221297).|  

## <a name="next-steps"></a>Следующие шаги

[Установка или удаление твердотельных в Reporting Services для SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
[Веб-часть средства просмотра на сайте SharePoint отчетов](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
[Викторина: Настройка служб SSRS 2012 для интеграции с SharePoint](http://go.microsoft.com/fwlink/?LinkId=306443)  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).

