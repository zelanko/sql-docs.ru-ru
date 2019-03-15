---
title: Что такое SQL Server Reporting Services (SSRS)? | Документы Майкрософт
description: Сведения о средствах и службах для создания мобильных отчетов и отчетов Reporting Services с разбивкой на страницы в локальной среде.
ms.date: 05/25/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services]
- SSRS
- reports [Reporting Services], about reports
- Reporting Services
- SQL Server Reporting Services
ms.assetid: b8d18d3d-9db0-43e7-8286-7b46cc3a37ed
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 08a71374d72a70e9bba6863eb9f6b5ac548d28f7
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56297402"
---
# <a name="what-is-sql-server-reporting-services-ssrs"></a>Что такое службы SQL Server Reporting Services (SSRS)?

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

Ищете сервер отчетов Power BI? См. статью [Что такое сервер отчетов Power BI?](https://docs.microsoft.com/power-bi/report-server/get-started)

Службы SQL Server Reporting Services (SSRS) предоставляют спектр готовых к использованию средств и служб для создания и развертывания мобильных отчетов и отчетов с разбиением на страницы в локальной среде, а также управления ими.

![Все службы SQL Server Reporting Services](../reporting-services/media/ss-reporting-services-all-together.png "Все службы SQL Server Reporting Services")

## <a name="create-deploy-and-manage-mobile-and-paginated-reports"></a>Создание и развертывание мобильных отчетов и отчетов с разбивкой на страницы, а также управление ими

Службы SQL Server Reporting Services — это решение, развертываемое клиентами в их локальной среде для создания, публикации отчетов и управления ими, а также для их доставки нужным пользователям разнообразными способами, например посредством просмотра в веб-браузере, на мобильном устройстве или в папке входящих сообщений электронной почты.

SQL Server Reporting Services предлагает обновленный набор продуктов:

* **"Традиционные" отчеты с разбиением на страницы** были обновлены, чтобы можно было создавать по-современному выглядящие отчеты с помощью обновленных средств и новых функций.
* **Новые мобильные отчеты** с гибким макетом, который адаптируется под различные устройства и способы их удержания.
* **Современный веб-портал** , который можно открыть в любом современном браузере. На новом портале можно упорядочивать и просматривать мобильные отчеты, отчеты с разбивкой на страницы и ключевые показатели эффективности Reporting Services. На портале также можно сохранять книги Excel.

Далее приведены более подробные сведения по каждому из этих аспектов.

### <a name="whats-new-in-reporting-services"></a>Новые возможности служб Reporting Services

В этих источниках приводятся актуальные сведения о новых возможностях SQLServer Reporting Services.

* [Новые возможности служб Reporting Services](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)
* [Блог команды разработки служб SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Канал Guy in a Cube на YouTube](https://www.youtube.com/channel/UCFp1vaKzpfvoGai0vE5VJ0w)

## <a name="paginated-reports"></a>Отчеты с разбиением на страницы

![ssrs-paginated-reports](../reporting-services/media/ssrs-paginated-reports.png)

Службы Reporting Services связаны с "традиционными" отчетами с разбиением на страницы, где при увеличении объема данных растет и число строк в таблицах, а также число страниц в отчете. Это удобно для создания выверенных документов с фиксированной разметкой, которые оптимизированы для печати, таких как файлы PDF и Word.

Данная рабочая нагрузка бизнес-аналитики сохранила актуальность и сейчас, поэтому мы улучшили ее. Теперь вы можете создавать по-современному выглядящие отчеты с обновленными и новыми функциями, используя [построитель отчетов](../reporting-services/report-builder/report-builder-in-sql-server-2016.md) или [конструктор отчетов в SQL Server Data Tools (SSDT)](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md).

* Мы обновили все стандартные цветовые палитры и стили по умолчанию, чтобы по умолчанию вы создавали отчеты в современном минималистическом стиле.
* Мы обновили на панель параметров, чтобы параметры можно было упорядочить любым удобным для вас образом.
* Вы можете выполнять экспорт в новые форматы, например PowerPoint. Визуализации Reporting Services в PowerPoint являются динамическими, а не просто снимками экрана, и доступны для изменения.
* Можно создать гибридную среду Power BI и Reporting Services:  вместо повторного создания локальных отчетов Reporting Services в Power BI вы можете закрепить визуальные элементы из этих отчетов на панелях мониторинга Power BI. Это позволит вам отслеживать все необходимое в одном месте на панели мониторинга Power BI.

## <a name="mobile-reports"></a>Мобильные отчеты

![ssrs-mobile-reports](../reporting-services/media/ssrs-mobile-reports.png)

Мобильные вычисления повлияли на те устройства, которые люди используют для работы, в результате чего изменились и требования к отчетам. Отчеты с фиксированным макетом плохо подходят для планшетов и телефонов. Вариант, предназначенный для большого экрана ПК, не является оптимальным на экране небольшого телефона, который еще и может иметь книжную либо альбомную ориентацию.

Для такого разнообразия форм-факторов нужен не фиксированный, а гибкий макет, который адаптируется под различные устройства и способы их удержания. Для этого мы добавили новый тип отчета — мобильные отчеты, основанные на технологии Datazen, которую мы приобрели около года назад и интегрировали в продукт. Имеющиеся у вас отчеты Datazen можно перенести в службы Reporting Services с помощью [помощника по миграции SQL Server для Datazen](https://www.microsoft.com/download/details.aspx?id=53128). 

Создать эти мобильные отчеты можно в новом приложении [издателя мобильных отчетов](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md) . После этого в собственных [приложениях Power BI для мобильных устройств](https://powerbi.microsoft.com/documentation/powerbi-power-bi-apps-for-mobile-devices/) на базе Windows 10, iOS, Android и HTML5 вы можете получить доступ к данным в облаке Power BI, а также к локальным данным SQL Server Reporting Services. При создании визуализаций издатель мобильных отчетов автоматически создает демонстрационные данные для каждой из них, чтобы вы могли узнать, как будет выглядеть визуализация с данными и какой тип данных подходит лучше всего.

## <a name="web-portal"></a>Веб-портал

![ssrs-web-portal](../reporting-services/media/ssrs-web-portal.png)

Для пользователей, работающих в основном режиме служб Reporting Services, представлен современный веб-портал, который можно открыть в любом современном браузере. На новом портале доступны все ваши мобильные отчеты, отчеты с разбивкой на страницы и ключевые показатели эффективности Reporting Services.

Веб-портал можно снабдить собственной фирменной символикой. Кроме того, можно создавать ключевые показатели эффективности непосредственно на веб-портале. Ключевые показатели эффективности позволяют быстро отслеживать основные бизнес-метрики в браузере без открытия отчета. 

Новый веб-портал является полностью переработанной версией диспетчера отчетов. Теперь это основанное на стандартах одностраничное приложение HTML5, под которое оптимизированы все наиболее распространенные современные браузеры, включая Microsoft Edge, Internet Explorer 10 и 11, Chrome, Firefox и Safari.

Содержимое на веб-портале упорядочивается по типу: мобильные отчеты Reporting Services и отчеты с разбивкой на страницы, ключевые показатели эффективности, книги Excel, общие наборы данных и общие источники данных для использования в качестве стандартных блоков отчетов. Портал обеспечивает их безопасное хранение и управление ими в виде традиционной иерархии папок. Вы можете пометить избранные элементы и управлять содержимым, если это входит в ваши обязанности.

На новом портале вы по-прежнему можете запланировать обработку отчетов, обращаться к отчетам по запросу и подписываться на опубликованные отчеты.

Подробнее о [веб-портале (собственный режим служб SSRS)](../reporting-services/web-portal-ssrs-native-mode.md).

## <a name="reporting-services-in-sharepoint-integrated-mode"></a>Службы Reporting Services в режиме интеграции с SharePoint

Отчеты публикуются в службах Reporting Services в режиме интеграции с SharePoint. Вы можете запланировать обработку отчетов, обратиться к ним по запросу, подписаться на опубликованные отчеты и экспортировать отчеты в другие приложения (например, Microsoft Excel). С помощью служб Reporting Services также можно создавать предупреждения об изменении данных в отчетах, опубликованных на сайте SharePoint, и получать электронные сообщения при изменении данных в отчете.  

Дополнительные сведения о [сервере отчетов служб Reporting Services в режиме интеграции с SharePoint](../reporting-services/report-server-sharepoint/reporting-services-report-server-sharepoint-mode.md).

## <a name="includessrsnoversionincludesssrsnoversion-mdmd-programming-features"></a>Возможности программирования[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 

Благодаря возможностям программирования [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] можно расширить и настроить функции создания отчетов с помощью интерфейсов API, которые позволяют интегрировать или расширить возможности обработки данных и отчетов в пользовательских приложениях.

Дополнительная [документация разработчика для служб Reporting Services](../reporting-services/reporting-services-developer-documentation.md). 

## <a name="next-steps"></a>Следующие шаги

* [Установка служб Reporting Services](../reporting-services/install-windows/install-reporting-services.md)  
* [Установка построителя отчетов](../reporting-services/install-windows/install-report-builder.md)   
* [Скачать SQL Server Data Tools (SSDT)](https://go.microsoft.com/fwlink/?LinkID=616714)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
