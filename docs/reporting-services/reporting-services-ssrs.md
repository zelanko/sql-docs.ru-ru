---
title: "Cлужбы Reporting Services (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "отчеты [Reporting Services]"
  - "Службы SSRS"
  - "отчеты [Reporting Services], об отчетах"
  - "Reporting Services"
  - "службы SQL Server Reporting Services"
ms.assetid: b8d18d3d-9db0-43e7-8286-7b46cc3a37ed
caps.latest.revision: 70
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Cлужбы Reporting Services (SSRS)
  Службы SQL Server Reporting Services (SSRS) предоставляют полный спектр готовых к использованию средств и служб для создания и развертывания мобильных отчетов и отчетов с разбиением на страницы в локальной среде, а также управления ими. 
  
 ![SQL Server Reporting Services all together](../reporting-services/media/ss-reporting-services-all-together.png "SQL Server Reporting Services all together")  
## <a name="what-is-sql-server-reporting-services-ssrs"></a>Что такое службы SQL Server Reporting Services (SSRS)?

Службы SQL Server Reporting Services — это решение, развертываемое клиентами в их локальной среде для создания, публикации отчетов и управления ими, а также для их доставки нужным пользователям разнообразными способами, например посредством просмотра в веб-браузере, на мобильном устройстве или в папке входящих сообщений электронной почты.

Для SQL Server 2016 службы Reporting Services предлагают обновленный набор продуктов.

* **"Традиционные" отчеты с разбиением на страницы** были обновлены, чтобы можно было создавать по-современному выглядящие отчеты с помощью обновленных средств и новых функций. 
* **Новые мобильные отчеты** с гибким макетом, который адаптируется под различные устройства и способы их удержания. 
* **Современный веб-портал**, который можно открыть в любом современном браузере. На новом портале можно организовывать и отображать мобильные отчеты и отчеты с разбиением на страницы, а также новые ключевые показатели эффективности. На портале также можно хранить книги Excel и отчеты Power BI Desktop. 

Далее приведены более подробные сведения по каждому из этих аспектов.
  
### <a name="whats-new-in-reporting-services"></a>Новые возможности служб Reporting Services

В этих источниках приводятся актуальные сведения о новых возможностях SQLServer 2016 Reporting Services. 
* [Новые возможности служб Reporting Services](../reporting-services/новые-возможности-служб-sql-server-reporting-services-ssrs.md)
* [Блог команды разработки служб SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Канал Guy in a Cube на YouTube](https://www.youtube.com/channel/UCFp1vaKzpfvoGai0vE5VJ0w)
  
## <a name="paginated-reports"></a>Отчеты с разбиением на страницы

![ssrs-paginated-reports](../reporting-services/media/ssrs-paginated-reports.png)

Службы Reporting Services связаны с "традиционными" отчетами с разбиением на страницы, где при увеличении объема данных растет и число строк в таблицах, а также число страниц в отчете. Это удобно для создания выверенных документов с фиксированной разметкой, которые оптимизированы для печати, таких как файлы PDF и Word. 

Данная рабочая нагрузка бизнес-аналитики сохранила актуальность и сейчас, поэтому мы улучшили ее. Теперь вы можете создавать по-современному выглядящие отчеты с обновленными и новыми функциями, используя [построитель отчетов](../reporting-services/report-builder/report-builder-in-sql-server-2016.md) или [конструктор отчетов в SQL Server Data Tools (SSDT)](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md). 

* Мы обновили все стандартные цветовые палитры и стили по умолчанию, чтобы по умолчанию вы создавали отчеты в современном минималистическом стиле.
* Мы обновили на панель параметров, чтобы параметры можно было упорядочить любым удобным для вас образом.
* Вы можете выполнять экспорт в новые форматы, например PowerPoint. Визуализации Reporting Services в PowerPoint являются динамическими, а не просто снимками экрана, и доступны для изменения.
* Можно создать гибридную среду Power BI/Reporting Services: вместо повторного создания локальных отчетов Reporting Services в Power BI вы можете закрепить визуальные элементы из этих отчетов на панелях мониторинга Power BI. Это позволит вам отслеживать все необходимое в одном месте на панели мониторинга Power BI.
 
## <a name="mobile-reports"></a>Мобильные отчеты

![ssrs-mobile-reports](../reporting-services/media/ssrs-mobile-reports.png)

Мобильные вычисления повлияли на те устройства, которые люди используют для работы, в результате чего изменились и требования к отчетам. Отчеты с фиксированным макетом плохо подходят для планшетов и телефонов. Вариант, предназначенный для большого экрана ПК, не является оптимальным на экране небольшого телефона, который еще и может иметь книжную либо альбомную ориентацию.

Для такого разнообразия форм-факторов нужен не фиксированный, а гибкий макет, который адаптируется под различные устройства и способы их удержания. Для этого мы добавили новый тип отчета — мобильные отчеты, основанные на технологии Datazen, которую мы приобрели около года назад и интегрировали в продукт. Имеющиеся у вас отчеты Datazen можно перенести в службы Reporting Services с помощью [помощника по миграции SQL Server для Datazen](https://www.microsoft.com/download/details.aspx?id=53128). 

Создать эти мобильные отчеты можно в новом приложении [издателя мобильных отчетов](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md). После этого в собственных [приложениях Power BI для мобильных устройств](https://powerbi.microsoft.com/documentation/powerbi-power-bi-apps-for-mobile-devices/) на базе Windows 10, iOS, Android и HTML5 вы можете получить доступ с данными в облаке Power BI, а также к локальным данным SQL Server 2016 Reporting Services. При создании визуализаций издатель мобильных отчетов автоматически создает демонстрационные данные для каждой из них, чтобы вы могли узнать, как будет выглядеть визуализация с данными и какой тип данных подходит лучше всего.

## <a name="web-portal"></a>Веб-портал

![ssrs-web-portal](../reporting-services/media/ssrs-web-portal.png)

Для пользователей, работающих в основном режиме служб Reporting Services, представлен современный веб-портал, который можно открыть в любом современном браузере. Там можно открыть все эти мобильные отчеты и отчеты с разбиением на страницы, а также новые ключевые показатели эффективности. Вы можете пометить избранные элементы и управлять содержимым, если это входит в ваши обязанности. 

Веб-портал можно снабдить собственной фирменной символикой. Кроме того, можно создавать ключевые показатели эффективности непосредственно на веб-портале. Ключевые показатели эффективности позволяют быстро отслеживать основные бизнес-метрики в браузере без открытия отчета. 

Новый веб-портал является полностью переработанной версией диспетчера отчетов. Теперь это основанное на стандартах одностраничное приложение HTML5, под которое оптимизированы все наиболее распространенные современные браузеры, включая Edge, Internet Explorer 10 и 11, Chrome, Firefox, Safari.

Веб-портал по-прежнему имеет традиционную иерархию папок, что позволяет упорядочить содержимое. Содержимое упорядочивается по типу: мобильные отчеты, ключевые показатели эффективности, отчеты с разбиением на страницы , а также отчеты Power BI Desktop, книги Excel, общие наборы данных и общие источники данных для использования в качестве стандартных блоков для отчетов. Здесь можно хранить их и управлять ими в полной безопасности.

На новом портале вы по-прежнему можете запланировать обработку отчетов, обращаться к отчетам по запросу и подписываться на опубликованные отчеты.

Дополнительные сведения о [веб-портале служб Reporting Services](../reporting-services/web-portal-ssrs-native-mode.md).
  
## <a name="reporting-services-in-sharepoint-integrated-mode"></a>Службы Reporting Services в режиме интеграции с SharePoint  

Отчеты публикуются в службах Reporting Services в режиме интеграции с SharePoint. Вы можете запланировать обработку отчетов, обратиться к ним по запросу, подписаться на опубликованные отчеты и экспортировать отчеты в другие приложения (например, Microsoft Excel). С помощью служб Reporting Services также можно создавать предупреждения об изменении данных в отчетах, опубликованных на сайте SharePoint, и получать электронные сообщения при изменении данных в отчете.  

Дополнительные сведения о [сервере отчетов служб Reporting Services в режиме интеграции с SharePoint](../reporting-services/report-server-sharepoint/reporting-services-report-server-sharepoint-mode.md).
 
## <a name="includessrsnoversiontokenssrsnoversionmdmd-programming-features"></a>Возможности программирования [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]  
 Благодаря возможностям программирования [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] можно расширить и настроить функции создания отчетов с помощью интерфейсов API, которые позволяют интегрировать или расширить возможности обработки данных и отчетов в пользовательских приложениях.
 
 Дополнительная [документация разработчика для служб Reporting Services](../reporting-services/reporting-services-developer-documentation.md). 
  
## <a name="browse-content-by-area"></a>Просмотр содержимого по области  
* [Обратная совместимость](../reporting-services/обратная-совместимость-службы-reporting-services.md) 
* [Сервер отчетов служб Reporting Services](../reporting-services/report-server-sharepoint/сервер-отчетов-служб-reporting-services.md)  
* [Веб-портал](../reporting-services/web-portal-ssrs-native-mode.md)
* [Отчеты служб Reporting Services &#40;SSRS&#41;](../reporting-services/reports/reporting-services-reports-ssrs.md)  
* [Данные отчета &#40;SSRS&#41;](../reporting-services/report-data/report-data-ssrs.md)  
* [Построитель отчетов в SQL Server 2016](../reporting-services/report-builder/report-builder-in-sql-server-2016.md)  
* [Издатель мобильных отчетов для SQL Server](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
* [Ключевые показатели эффективности в службах Reporting Services](../reporting-services/working-with-kpis-in-reporting-services.md)
* [Инструментальные средства служб Reporting Services](../reporting-services/tools/reporting-services-tools.md)  
  
## <a name="see-also"></a>См. также:  
* [Установка служб Reporting Services](../reporting-services/install-windows/install-reporting-services.md)
* [Установка построителя отчетов](../reporting-services/install-windows/install-report-builder.md)   
* [Скачать SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)
  
  