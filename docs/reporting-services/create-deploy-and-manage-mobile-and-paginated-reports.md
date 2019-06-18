---
title: Что такое SQL Server Reporting Services (SSRS)? | Документы Майкрософт
description: Сведения о средствах и службах для создания мобильных отчетов и отчетов Reporting Services с разбивкой на страницы в локальной среде.
ms.date: 05/06/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services]
- SSRS
- reports [Reporting Services], about reports
- Reporting Services
- SQL Server Reporting Services
ms.assetid: b8d18d3d-9db0-43e7-8286-7b46cc3a37ed
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 26fa81278afd686d25192fdd49bbc3f2119a5762
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65571570"
---
# <a name="what-is-sql-server-reporting-services-ssrs"></a>Что такое службы SQL Server Reporting Services (SSRS)?

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

Ищете сервер отчетов Power BI? См. статью [Что такое сервер отчетов Power BI?](https://docs.microsoft.com/power-bi/report-server/get-started)

Службы SQL Server Reporting Services (SSRS) предоставляют набор локальных средств и служб для создания и развертывания мобильных отчетов и отчетов с разбиением на страницы, а также управления ими.

![Все службы SQL Server Reporting Services](../reporting-services/media/ss-reporting-services-all-together.png "Все службы SQL Server Reporting Services")

## <a name="create-deploy-and-manage-mobile-and-paginated-reports"></a>Создание и развертывание мобильных отчетов и отчетов с разбивкой на страницы, а также управление ими

Решение SSRS гибко доставляет нужную информацию нужным пользователям. Пользователи могут получать отчеты через веб-браузер на мобильном устройстве или по электронной почте.

SQL Server Reporting Services предлагает обновленный набор продуктов:

* **"Традиционные" отчеты с разбиением на страницы** были обновлены, чтобы можно было создавать по-современному выглядящие отчеты с помощью обновленных средств и новых функций.
* **Новые мобильные отчеты** с гибким макетом, который адаптируется под различные устройства и способы их удержания.
* **Современный веб-портал** , который можно открыть в любом современном браузере. На новом портале можно упорядочивать и просматривать мобильные отчеты, отчеты с разбивкой на страницы и ключевые показатели эффективности Reporting Services. На портале также можно сохранять книги Excel.

Далее приведены более подробные сведения по каждому из этих аспектов.

### <a name="whats-new-in-reporting-services"></a>Новые возможности служб Reporting Services

Эти источники предоставят вам актуальные сведения о новых возможностях SQL Server Reporting Services.

* [Новые возможности служб Reporting Services](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)
* [Блог команды разработки служб SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Канал Guy in a Cube на YouTube](https://www.youtube.com/channel/UCFp1vaKzpfvoGai0vE5VJ0w)

## <a name="paginated-reports"></a>Отчеты с разбиением на страницы

![ssrs-paginated-reports](../reporting-services/media/ssrs-paginated-reports.png)

С помощью Reporting Services создаются "традиционные" отчеты с разбивкой на страницы, которые идеально подходят для оптимизированных для печати документов с фиксированным макетом таких форматов, как PDF и Word.

Данная рабочая нагрузка бизнес-аналитики сохранила актуальность и сейчас, поэтому мы улучшили ее. Теперь вы можете создавать современного вида отчеты с новыми функциями, используя построитель отчетов или [SQL Server Data Tools (SSDT)](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md).

* Мы обновили все стандартные цветовые палитры и стили по умолчанию, чтобы по умолчанию вы создавали отчеты в современном минималистическом стиле.
* Мы обновили на панель параметров, чтобы параметры можно было упорядочить любым удобным для вас образом.
* Вы можете выполнять экспорт в новые форматы, например PowerPoint. Визуализации Reporting Services в PowerPoint являются динамическими, а не просто снимками экрана, и доступны для изменения.
* Можно создать гибридную среду Power BI/Reporting Services: вместо повторного создания локальных отчетов Reporting Services в Power BI вы можете закрепить визуальные элементы из этих отчетов на панелях мониторинга Power BI. Это позволит вам отслеживать все необходимое в одном месте на панели мониторинга Power BI.

## <a name="mobile-reports"></a>Мобильные отчеты

![ssrs-mobile-reports](../reporting-services/media/ssrs-mobile-reports.png)

Мобильные вычисления повлияли на те устройства, которые люди используют для работы, в результате чего изменились и требования к отчетам. Отчеты с фиксированным макетом плохо подходят для планшетов и телефонов. Вариант, предназначенный для большого экрана ПК, не является оптимальным на экране небольшого телефона, который еще и может иметь книжную либо альбомную ориентацию.

Для такого разнообразия форм-факторов нужен не фиксированный, а изменяемый макет, который адаптируется под разные размеры и ориентации экранов. Для этого мы добавили новый тип отчета — мобильные отчеты, основанные на технологии Datazen, которую мы приобрели около года назад и интегрировали в продукт. Имеющиеся у вас отчеты Datazen можно перенести в службы Reporting Services с помощью [помощника по миграции SQL Server для Datazen](https://www.microsoft.com/download/details.aspx?id=53128).

Создать эти мобильные отчеты можно в новом приложении [издателя мобильных отчетов](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md) . После этого вы сможете в собственных [приложениях Power BI для мобильных устройств](https://powerbi.microsoft.com/documentation/powerbi-power-bi-apps-for-mobile-devices/) на базе Windows 10, iOS, Android и HTML5 получать доступ к данным из Power BI, облака или служб SQL Server Reporting Services.

При создании визуализаций издатель мобильных отчетов автоматически создает пример данных. Это позволяет понять, как будет выглядеть визуализация с реальными данными и какой тип данных подходит для нее лучше всего.

## <a name="web-portal"></a>Веб-портал

![ssrs-web-portal](../reporting-services/media/ssrs-web-portal.png)

Для пользователей, которые работают в собственном режиме служб Reporting Services, интерфейсом служит современный веб-портал, который можно открыть в большинстве браузеров. На новом портале доступны все мобильные отчеты, отчеты с разбивкой на страницы и ключевые показатели эффективности служб Reporting Services. Ключевые показатели эффективности позволяют быстро отслеживать основные бизнес-метрики в браузере без открытия отчета.

Новый веб-портал является полностью переработанной версией диспетчера отчетов. Теперь это основанное на стандартах одностраничное приложение стандарта HTML5, под который оптимизированы все современные браузеры, включая Microsoft Edge, Internet Explorer 10 и 11, Chrome, Firefox, Safari.

Содержимое на веб-портале упорядочивается по типу:

* отчеты с разбиением на страницы;
* мобильные отчеты; 
* Ключевые показатели эффективности
* книги Excel;
* общие наборы данных;
* общие источники данных

Портал обеспечивает их безопасное хранение и управление ими в виде традиционной иерархии папок. Поместите отчеты в "Избранное" для быстрого доступа. Имея необходимые разрешения, вы сможете управлять содержимым SSRS.

На новом портале вы по-прежнему можете запланировать обработку отчетов, открыть отчеты по запросу или подписаться на опубликованные отчеты.

См. дополнительные сведения о [веб-портале](../reporting-services/web-portal-ssrs-native-mode.md).

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

## <a name="reporting-services-in-sharepoint-integrated-mode"></a>Службы Reporting Services в режиме интеграции с SharePoint

Отчеты публикуются в службах Reporting Services в режиме интеграции с SharePoint. Вы можете запланировать обработку отчетов, обратиться к ним по запросу, подписаться на опубликованные отчеты и экспортировать отчеты в другие приложения (например, Microsoft Excel). С помощью служб Reporting Services также можно создавать предупреждения об изменении данных в отчетах, опубликованных на сайте SharePoint, и получать электронные сообщения при изменении данных в отчете.  

Дополнительные сведения о [сервере отчетов служб Reporting Services в режиме интеграции с SharePoint](../reporting-services/report-server-sharepoint/reporting-services-report-server-sharepoint-mode.md).

::: moniker-end

## <a name="includessrsnoversionincludesssrsnoversion-mdmd-programming-features"></a>Возможности программирования[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]

Возможности программирования [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] позволяют вам расширять и настраивать функции для работы с отчетами. Используйте API-интерфейсы служб SSRS для интеграции или расширения данных и обработки отчетов в пользовательских приложениях.

Дополнительная [документация разработчика для служб Reporting Services](../reporting-services/reporting-services-developer-documentation.md).

## <a name="next-steps"></a>Следующие шаги

* [Установка служб Reporting Services](../reporting-services/install-windows/install-reporting-services.md)
* [Скачать SQL Server Data Tools (SSDT)](https://go.microsoft.com/fwlink/?LinkID=616714)
* [Установка построителя отчетов](../reporting-services/install-windows/install-report-builder.md)

* Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
