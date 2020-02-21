---
title: Сервер отчетов служб Reporting Services (режим интеграции с SharePoint) | Документы Майкрософт
ms.date: 09/26/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
monikerRange: '>=sql-server-2016 <=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: af25232f5a1603f25814309270813188c05a89fc
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "68262351"
---
# <a name="reporting-services-report-server-sharepoint-mode"></a>Сервер отчетов служб Reporting Services (режим SharePoint)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  Сервер отчетов служб Reporting Services, настроенный для работы в **режиме интеграции с SharePoint**, может выполняться в среде, в которой развернут продукт SharePoint. Сервер отчетов в режиме интеграции с SharePoint может использовать функции совместной работы и управления SharePoint для отчетов и других типов содержимого [!INCLUDE[ssRSnfoversion_md](../../includes/ssrsnoversion-md.md)] . Для режима интеграции с SharePoint необходимо установить соответствующую версию надстройки служб Reporting Services для продуктов SharePoint на компьютеры с клиентским веб-интерфейсом SharePoint.  
  
> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.

 Дополнительные сведения об установке и настройке см. в следующем документе.  
  
-   [Установка служб Reporting Services в режиме интеграции с SharePoint для SharePoint 2010](https://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c).  
  
-   [Добавление дополнительного сервера отчетов в ферму](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
## <a name="feature-summary"></a>Сводка по функциям

 Настройка сервера отчетов для работы в режиме интеграции с SharePoint предоставляет следующие дополнительные возможности (доступные только при развертывании в этом режиме).  
  
-   Функции управления документами и совместной работы SharePoint, включая обработку предупреждений. Сайт SharePoint предоставляет единый портал для доступа ко всем документам и единую точку управления элементами отчета.  
  
-   Использование разрешений SharePoint и поставщиков служб проверки подлинности для управления доступом к отчетам, моделям и другим элементам.  
  
-   Топология развертывания SharePoint используется для распределения отчетов по Интернет-соединению за пределами брандмауэра. Сервер отчетов поддерживает службы обработки отчетов и данных в контексте более крупной конфигурации SharePoint, настроенной для доступа в Интернет.  
  
-   Управление отчетами, моделями, источниками данных, расписаниями и журналом отчетов с помощью пользовательских страниц приложений на сайте SharePoint. На сайте SharePoint можно задавать свойства, создавать расписания, оформлять подписки, а также создавать и вести журнал отчетов, используя те же методы, что и при работе с другими средствами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Публикация и передача отчетов, моделей отчетов, ресурсов и общих источников данных в библиотеку SharePoint, в том числе центр отчетов на сервере Office SharePoint.  
  
     Для создания отчетов и источников данных, которые будут публиковаться непосредственно в библиотеке SharePoint, используйте конструктор отчетов, конструктор моделей и построитель отчетов. Также можно использовать действие «Передача» на сайте SharePoint, чтобы добавить в библиотеку SharePoint любые определения отчетов и модели отчетов.  
  
     Сервер отчетов всегда обрабатывает определения отчетов одинаковым образом, независимо от используемого режима сервера, и режим сервера не влияет на данные отчета и его макет. Любой отчет, который может запускаться на сервере отчетов в собственном режиме, может запускаться и на сервере отчетов, настроенном для работы в режиме интеграции с SharePoint.  
  
-   Оформление подписки и доставка отчетов в библиотеку SharePoint с помощью нового модуля доставки SharePoint. Также можно доставлять отчеты по электронной почте или в общую папку. Для доставки отчетов применяются модули доставки сервера отчетов. Можно создать управляемые данными подписки для крупномасштабного распространения отчетов с использованием сведений о подписчике, запрошенных во время выполнения.  
  
-   Для просмотра отчета в веб-приложении SharePoint можно добавить веб-часть "Средство просмотра отчетов". В эту веб-часть входят средства перемещения по страницам, а также функции поиска, печати и экспорта.  
  
-   Программирование в контексте новой конечной точки SOAP для создания пользовательских приложений, интегрируемых с сайтом SharePoint. Также можно использовать обновленный поставщик инструментария управления Windows (WMI) для программной настройки экземпляра сервера отчетов, работающего в режиме интеграции с SharePoint.  
  
-   Отчеты Microsoft Access в подключенном режиме.  
  
-   AAM-зоны, развертывания, направленные в сторону Интернета, и токены пользователя SharePoint для списков SharePoint.  
  
## <a name="connected-mode-and-local-mode"></a>Подключенный и локальный режимы

 В выпуске SQL Server 2008 R2 введен новый *локальный режим* для просмотра отчетов с сервера SharePoint 2010 с установленной надстройкой служб Microsoft SQL Server 2008 R2 Reporting Services (или более поздней версии) для продуктов SharePoint 2010.  
  
-   *Локальный режим*. Локальный режим позволяет подготавливать отчеты локально из библиотеки документов SharePoint без интеграции с сервером отчетов служб Reporting Services. Надстройка служб Reporting Services для продуктов SharePoint является обязательной, в отличие от сервера отчетов служб Reporting Services. Надстройка может быть установлена несколькими различными способами, в том числе с помощью средства подготовки продуктов SharePoint 2010. Дополнительные сведения о локальном режиме см. в разделах [Отчеты, созданные в локальном и подключенном режимах в средстве просмотра отчетов](../../reporting-services/report-server-sharepoint/local-mode-vs-connected-mode-reports-in-the-report-viewer.md) и [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
-   *Подключенный режим*. Подключенный режим поддерживается путем включения сервера отчетов служб Reporting Services в ферму SharePoint с помощью центра администрирования SharePoint. Интеграция с сервером отчетов обеспечивает полные возможности для работы, в том числе функций совместной работы SharePoint 2010 и серверные функции сервера отчетов: подписки, моментальные снимки и серверная обработка.  
  
## <a name="unsupported-sharepoint-features"></a>Неподдерживаемые функции SharePoint

 При работе в режиме интеграции доступны не все компоненты SharePoint. Далее приведен список компонентов SharePoint, с которыми службы Reporting Services не интегрируются напрямую.  
  
-   Служба Secure Store.  
  
-   Нельзя использовать интеграцию с календарем SharePoint Outlook и создавать расписания SharePoint для файлов служб отчетов в библиотеке документов.  
  
-   Каталог SharePoint Business Data.  
  
-   Возможность персонализации SharePoint также не поддерживается на страницах служб Reporting Services. Интеграция с сервером отчетов невозможна, если веб-приложение SharePoint включено для анонимного доступа.  
  
-   Службы SQL Server Reporting Services **не** поддерживают управление версиями библиотеки документов SharePoint. Если сохранить элементы отчета в библиотеке документов, для которой включена функция "История версий документов", то функции службы Reporting Services будут работать неправильно и в журнале ULS будут формироваться ошибки. В следующем примере показана ошибка в журнале ULS:  
  
    -   "...отключен источник данных, связанный с отчетом".  
  
     История версий документов библиотеки настраивается на странице "Параметры версий" окна "Параметры библиотеки".  
  
## <a name="supported-combinations-of-the-sharepoint-add-in-and-report-server"></a>Поддерживаемые сочетания надстройки SharePoint и сервера отчетов

 Не все функции поддерживаются во всех сочетаниях сервера отчетов, надстройки служб Reporting Services для SharePoint и продуктов SharePoint. Дополнительные сведения см. в разделе [Поддерживаемые сочетания SharePoint, компонентов служб Reporting Services и надстроек](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md).  
  
> [!NOTE]  
>  Правильная версия надстройки служб Reporting Services должна использоваться с соответствующей версией продуктов SharePoint.  
  
## <a name="components-that-provide-integration"></a>Обеспечивающие интеграцию компоненты

 Для объединения серверов в одном развертывании следует интегрировать установку служб Reporting Services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с экземпляром продуктов SharePoint  
  
 Интеграция предоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и надстройкой служб Reporting Services для продуктов SharePoint. Надстройка служб Reporting Services является свободно распространяемым компонентом, который можно скачать и установить на сервер с соответствующей версией SharePoint.  
  
> [!TIP]  
>  Не все функции поддерживаются во всех сочетаниях сервера отчетов, надстройки служб Reporting Services для SharePoint и продуктов SharePoint. Дополнительные сведения см. в разделе [Поддерживаемые сочетания SharePoint, компонентов служб Reporting Services и надстроек](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md).  
  
-   На сервере SharePoint надстройка служб Reporting Services предоставляет конечную точку прокси для сервера отчетов, веб-часть средства просмотра отчетов и страницы приложений для просмотра содержимого сервера отчетов, его хранения и управления им на сайте SharePoint или в ферме SharePoint.  
  
-   Службы Reporting Services предоставляют обновленные файлы программ, конечную точку SOAP и пользовательские модули безопасности и доставки. Сервер отчетов должен быть настроен для работы в режиме интеграции с SharePoint, специально выделенном для поддержки доступа к отчетам и их доставки через сайт SharePoint.  
  
 После установки надстройки служб Reporting Services в SharePoint и настройки обоих серверов для интеграции можно передать или опубликовать типы содержимого сервера отчетов в библиотеке SharePoint, а затем просматривать эти документы и управлять ими с сайта SharePoint. Передача или публикация содержимого сервера отчетов является важным первым шагом. Веб-часть и страницы становятся доступны при выборе определений отчетов (RDL), моделей отчетов (SMDL) и источников общих данных (RSDS) на сайте SharePoint.  
  
##  <a name="language-considerations"></a>Дополнительные сведения

 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] и [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] поддерживают гораздо больше языков, чем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Если настроить сервер отчетов для работы с развертыванием продукта SharePoint, можно получить сочетание языков. Далее описано, какой язык будут иметь пользовательский интерфейс, документация и сообщения.  
  
- Все страницы приложений, средства, сообщения об ошибках и предупреждения, создаваемые службами Reporting Services, будут выводиться на языке, используемом экземпляром служб Reporting Services (это один из языков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).  
  
- Страницы приложения, открываемые на сайте SharePoint, веб-часть средства просмотра отчетов и построитель отчетов отображаются на одном из языков, поддерживаемых для надстройки служб Reporting Services. Список поддерживаемых языков см. в [скачиваемых материалах по SQL Server](https://msdn.microsoft.com/sql/downloads/) и на странице скачивания надстройки для служб SQL Server 2016 Reporting Services.  
  
- Сайты и центр администрирования SharePoint, справка в Интернете и сообщения доступны на языках, поддерживаемых продуктами Office Server.  
  
 Если язык, используемый продуктом или технологией SharePoint, отличается от языка сервера отчетов, службы Reporting Services будут использовать язык из той же языковой группы, который ближе всего к языку SharePoint. Если подходящий язык недоступен, сервер отчетов будет использовать английский язык.  
  
## <a name="related-tasks"></a>Связанные задачи

 В приведенной ниже таблице перечислены задачи, связанные с сервером отчетов служб Reporting Services в режиме интеграции с SharePoint.  
  
|**Задача**|**Ссылка**|  
|--------------|--------------|  
|Подробные инструкции по установке и настройке служб Reporting Services в режиме интеграции с SharePoint.|[Установка служб Reporting Services в режиме SharePoint для SharePoint 2010](https://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c) и [Добавление дополнительного сервера отчетов в ферму](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md).|  
|Горизонтально масштабируемое развертывание служб Reporting Services в SharePoint путем добавления дополнительных серверов отчетов.|[Добавление дополнительного сервера отчетов в ферму](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) и [Топологии развертывания для компонентов бизнес-аналитики SQL Server в SharePoint](https://msdn.microsoft.com/library/39f76bc7-94e6-4dbc-bfa5-d56f4430bb26).|  
|Добавление дополнительных клиентских веб-интерфейсов SharePoint с установленными компонентами Reporting Services для просмотра элементов отчетов.|[Добавление дополнительного клиентского веб-интерфейса служб Reporting Services в ферме](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)|  
|Настройка электронной почты для сервера отчетов в среде SharePoint.|[Настройка электронной почты для приложения служб Reporting Services](../install-windows/configure-e-mail-for-a-reporting-services-service-application.md)|
|Последние сведения об этом выпуске доступны на TechNet Wiki.|[Рекомендации, советы и сведения по устранению неполадок служб SQL Server 2012 Reporting Services](https://go.microsoft.com/fwlink/?LinkId=221297).|  

## <a name="next-steps"></a>Дальнейшие действия

[Установка или удаление надстройки служб Reporting Services для SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)
[Веб-часть "Средство просмотра отчетов" на сайте SharePoint (службы Reporting Services)](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
