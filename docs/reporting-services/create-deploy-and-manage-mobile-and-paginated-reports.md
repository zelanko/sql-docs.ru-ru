---
title: "Службы Reporting Services (SSRS) | Документы Microsoft"
description: "Дополнительные сведения о средствах и службах для мобильных устройств и разбиением на страницы отчетов служб Reporting Services и отчеты Power BI на локальном компьютере."
ms.custom: 
ms.date: 07/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- reports [Reporting Services]
- SSRS
- reports [Reporting Services], about reports
- Reporting Services
- SQL Server Reporting Services
ms.assetid: b8d18d3d-9db0-43e7-8286-7b46cc3a37ed
caps.latest.revision: 70
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 49f990d30564a2c4fc38a527e7da1e97f9a21ca1
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---

# <a name="what-is-sql-server-reporting-services-ssrs"></a>Что такое службы SQL Server Reporting Services (SSRS)?

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

Создавать, развертывать и управлять мобильными и разбиением на страницы отчетов служб Reporting Services и отчеты Power BI на локальном компьютере спектр готовых к использованию средств и служб, предоставляющих службы SQL Server Reporting Services (SSRS) и Power BI.

![SQL Server Reporting Services все вместе](../reporting-services/media/ss-reporting-services-all-together.png "SQL Server Reporting Services все вместе")

## <a name="create-deploy-and-manage-mobile-and-paginated-reports"></a>Создавать, развертывать и управлять отчетами мобильных и разбиением на страницы

Службы SQL Server Reporting Services — это решение, развертываемое клиентами в их локальной среде для создания, публикации отчетов и управления ими, а также для их доставки нужным пользователям разнообразными способами, например посредством просмотра в веб-браузере, на мобильном устройстве или в папке входящих сообщений электронной почты.

Для SQL Server 2016 службы Reporting Services предлагают обновленный набор продуктов.

* **"Традиционные" отчеты с разбиением на страницы** были обновлены, чтобы можно было создавать по-современному выглядящие отчеты с помощью обновленных средств и новых функций.
* **Новые мобильные отчеты** с гибким макетом, который адаптируется под различные устройства и способы их удержания.
* **Современный веб-портал** , который можно открыть в любом современном браузере. На новом портале можно организовать и отображения мобильных и разбиением на страницы отчетов служб Reporting Services и ключевые показатели эффективности, а также отчеты Power BI Desktop. Можно также сохранить книги Excel на портале.

Далее приведены более подробные сведения по каждому из этих аспектов.

> [!NOTE]
> Ищете сервера Power BI отчетов? В разделе [приступить к работе с сервером отчетов Power BI](https://powerbi.microsoft.com/documentation/reportserver-get-started/).

### <a name="whats-new-in-reporting-services"></a>Новые возможности служб Reporting Services

В этих источниках приводятся актуальные сведения о новых возможностях SQLServer 2016 Reporting Services.

* [Новые возможности служб Reporting Services](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)
* [Блог команды разработки служб SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Канал Guy in a Cube на YouTube](https://www.youtube.com/channel/UCFp1vaKzpfvoGai0vE5VJ0w)

## <a name="paginated-reports"></a>Отчеты с разбиением на страницы

![ssrs-paginated-reports](../reporting-services/media/ssrs-paginated-reports.png)

Службы Reporting Services связаны с "традиционными" отчетами с разбиением на страницы, где при увеличении объема данных растет и число строк в таблицах, а также число страниц в отчете. Это удобно для создания выверенных документов с фиксированной разметкой, которые оптимизированы для печати, таких как файлы PDF и Word.

Данная рабочая нагрузка бизнес-аналитики сохранила актуальность и сейчас, поэтому мы улучшили ее. Теперь можно создавать отчеты, оформленные в современном с обновленной новыми функциями, используя [построитель](../reporting-services/report-builder/report-builder-in-sql-server-2016.md) или конструктор отчетов в [SQL Server Data Tools (SSDT)](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md).

* Мы обновили все стандартные цветовые палитры и стили по умолчанию, чтобы по умолчанию вы создавали отчеты в современном минималистическом стиле.
* Мы обновили на панель параметров, чтобы параметры можно было упорядочить любым удобным для вас образом.
* Вы можете выполнять экспорт в новые форматы, например PowerPoint. Визуализации Reporting Services в PowerPoint являются динамическими, а не просто снимками экрана, и доступны для изменения.
* Можно создать гибридную среду Power BI/Reporting Services: вместо повторного создания локальных отчетов Reporting Services в Power BI вы можете закрепить визуальные элементы из этих отчетов на панелях мониторинга Power BI. Это позволит вам отслеживать все необходимое в одном месте на панели мониторинга Power BI.

## <a name="mobile-reports"></a>Мобильные отчеты

![ssrs-mobile-reports](../reporting-services/media/ssrs-mobile-reports.png)

Мобильные вычисления повлияли на те устройства, которые люди используют для работы, в результате чего изменились и требования к отчетам. Отчеты с фиксированным макетом плохо подходят для планшетов и телефонов. Вариант, предназначенный для большого экрана ПК, не является оптимальным на экране небольшого телефона, который еще и может иметь книжную либо альбомную ориентацию.

Для такого разнообразия форм-факторов нужен не фиксированный, а гибкий макет, который адаптируется под различные устройства и способы их удержания. Для этого мы добавили новый тип отчета — мобильные отчеты, основанные на технологии Datazen, которую мы приобрели около года назад и интегрировали в продукт. Имеющиеся у вас отчеты Datazen можно перенести в службы Reporting Services с помощью [помощника по миграции SQL Server для Datazen](https://www.microsoft.com/download/details.aspx?id=53128). 

Создать эти мобильные отчеты можно в новом приложении [издателя мобильных отчетов](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md) . После этого в собственных [приложениях Power BI для мобильных устройств](https://powerbi.microsoft.com/documentation/powerbi-power-bi-apps-for-mobile-devices/) на базе Windows 10, iOS, Android и HTML5 вы можете получить доступ с данными в облаке Power BI, а также к локальным данным SQL Server 2016 Reporting Services. При создании визуализаций издатель мобильных отчетов автоматически создает демонстрационные данные для каждой из них, чтобы вы могли узнать, как будет выглядеть визуализация с данными и какой тип данных подходит лучше всего.

## <a name="web-portal"></a>Веб-портал

![ssrs-web-portal](../reporting-services/media/ssrs-web-portal.png)

Для пользователей, работающих в основном режиме служб Reporting Services, представлен современный веб-портал, который можно открыть в любом современном браузере. Можно использовать отчеты служб Reporting Services мобильных и разбиением на страницы и ключевых показателей эффективности в новый портал, а также отчеты Power BI Desktop. Дополнительные сведения о [отчетов Power BI в службах Reporting Services](../reporting-services/power-bi-reports-in-reporting-services.md).  

Веб-портал можно снабдить собственной фирменной символикой. Кроме того, можно создавать ключевые показатели эффективности непосредственно на веб-портале. Ключевые показатели эффективности позволяют быстро отслеживать основные бизнес-метрики в браузере без открытия отчета. 

Новый веб-портал является полностью переработанной версией диспетчера отчетов. Теперь это основанное на стандартах одностраничное приложение HTML5, под которое оптимизированы все наиболее распространенные современные браузеры, включая Edge, Internet Explorer 10 и 11, Chrome, Firefox, Safari.

Содержимое на веб-портале упорядочено по типу: мобильных и разбиением на страницы отчетов служб Reporting Services и ключевых показателей эффективности, а также Power BI Desktop отчеты, Excel книги, общие наборы данных и общих источников данных для использования в качестве стандартных блоков для отчетов. Можно хранить и ими безопасно здесь, в иерархии папок традиционных. Вы можете пометить избранные элементы и управлять содержимым, если это входит в ваши обязанности.

На новом портале вы по-прежнему можете запланировать обработку отчетов, обращаться к отчетам по запросу и подписываться на опубликованные отчеты.

Дополнительные сведения о [веб-портал (основной режим служб SSRS)](../reporting-services/web-portal-ssrs-native-mode.md).

## <a name="reporting-services-in-sharepoint-integrated-mode"></a>Службы Reporting Services в режиме интеграции с SharePoint

Отчеты публикуются в службах Reporting Services в режиме интеграции с SharePoint. Вы можете запланировать обработку отчетов, обратиться к ним по запросу, подписаться на опубликованные отчеты и экспортировать отчеты в другие приложения (например, Microsoft Excel). С помощью служб Reporting Services также можно создавать предупреждения об изменении данных в отчетах, опубликованных на сайте SharePoint, и получать электронные сообщения при изменении данных в отчете.  

Дополнительные сведения о [сервере отчетов служб Reporting Services в режиме интеграции с SharePoint](../reporting-services/report-server-sharepoint/reporting-services-report-server-sharepoint-mode.md).

## <a name="includessrsnoversionincludesssrsnoversion-mdmd-programming-features"></a>Возможности программирования[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 

Благодаря возможностям программирования [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] можно расширить и настроить функции создания отчетов с помощью интерфейсов API, которые позволяют интегрировать или расширить возможности обработки данных и отчетов в пользовательских приложениях.

Дополнительная [документация разработчика для служб Reporting Services](../reporting-services/reporting-services-developer-documentation.md). 

## <a name="next-steps"></a>Следующие шаги

* [Установка служб Reporting Services](../reporting-services/install-windows/install-reporting-services.md)  
* [Установка построителя отчетов](../reporting-services/install-windows/install-report-builder.md)   
* [Скачать SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)  
* [В службах Reporting Services в отчетах Power BI](../reporting-services/power-bi-reports-in-reporting-services.md)

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
