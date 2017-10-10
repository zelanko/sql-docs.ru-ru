---
title: "Веб-часть средства просмотра на сайте SharePoint отчетов | Документы Microsoft"
ms.custom: 
ms.date: 09/25/2017
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
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: a37ed5efe7c365c601deb95d9fe761d227e7021e
ms.contentlocale: ru-ru
ms.lasthandoff: 10/06/2017

---
# <a name="report-viewer-web-part-on-a-sharepoint-site"></a>Веб-часть средства просмотра на сайте SharePoint отчетов

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Веб-часть средства просмотра отчетов имеет настраиваемые веб-части. Веб-части, чтобы просматривать, печатать и экспортировать отчеты на сервере отчетов на сайте SharePoint. Веб-часть средства просмотра отчетов связан с файлы определения отчетов (RDL), обрабатываемых сервером отчетов Microsoft SQL Server Reporting Services. 

Последние веб-части средства просмотра отчетов можно также с разбиением на страницы службы отчетов, развернутых на сервере отчетов Power BI. Веб-часть не работает с Power BI с отчетами.

## <a name="why-the-report-viewer-web-part-is-re-introduced"></a>Почему веб-части средства просмотра отчетов станет доступен

Веб-часть средства просмотра отчетов был доступен в рамках надстройки служб Reporting Services для продуктов SharePoint. Веб-части была подходящим для серверов отчетов в режиме интеграции с SharePoint. Режим интеграции с SharePoint был объявлен устаревшим после SQL Server 2016.

Начиная с SQL Server 2017 г., имеется только один режим установки для служб Reporting Services: **собственный режим**. Можно внедрить все типы отчетов, с помощью части веб-просмотра страниц с помощью *rs: внедрить = true* параметра URL-адреса. Внедрение отчетов на страницы SharePoint является истории интеграции, запрашиваемых клиентами и обновленные веб-части средства просмотра отчетов поддерживает такие сценарии для отчетов с разбиением на страницы.

Хотя веб-части средства просмотра страницы суффиксы для внедрения разбиением на страницы отчетов в страницу SharePoint, обновленные веб-части средства просмотра отчетов предлагает дополнительные функции.

* Показать или скрыть кнопки определенной панели инструментов
* Переопределить значения параметров отчета
* Подключение веб-части фильтра на параметры отчета

## <a name="download-the-report-viewer-web-part-solution-package"></a>Загрузка пакета средства просмотра отчетов веб-части решения

Веб-часть средства просмотра отчетов доступен в центре загрузки Майкрософт.

[Загрузка пакета решения веб-части средства просмотра отчетов](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="considerations-and-limitations"></a>Рекомендации и ограничения

Перечисленные элементы относятся к обновленной веб-части средства просмотра отчетов.

* Веб-часть может быть использован только для *классический* страницы SharePoint.
* Для внедрения в веб-части средства просмотра отчетов поддерживаются только разбиением на страницы отчетов (RDL). Если вам нужна для внедрения отчетов Power BI или мобильные отчеты, можно использовать *rs: внедрить = true* параметра URL-адреса.

## <a name="next-steps"></a>Следующие шаги

Чтобы приступить к работе с обновленной веб-части средства просмотра отчетов, см. [развертывание веб-части средства просмотра отчетов на сайте SharePoint](deploy-report-viewer-web-part.md).
