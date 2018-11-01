---
title: Создание мобильных отчетов с помощью издателя мобильных отчетов SQL Server | Документы Майкрософт
description: Ознакомьтесь со сведениями о мобильных отчетах служб Reporting Services для мобильных устройств, подключенных к локальным данным и содержащих различные визуализации данных.
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: a5a8dbf6-4c3a-435d-8188-d6656c32f229
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4572d5c325dbfb36a17ce2c987140ab56b6626e6
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50031633"
---
# <a name="create-mobile-reports-with-sql-server-mobile-report-publisher"></a>Создание мобильных отчетов с помощью издателя мобильных отчетов SQL Server
Ознакомьтесь со сведениями о мобильных отчетах [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , оптимизированных для мобильных устройств, подключенных к локальным данным и содержащих различные визуализации данных. 

>[!NOTE]
>  Нужно ли вам переносить содержимое сервера Datazen, например панели мониторинга и ключевые показатели эффективности, на сервер SQL Server 2016 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]? Воспользуйтесь [помощником по миграции SQL Server для Datazen](https://www.microsoft.com/en-us/download/details.aspx?id=53128). 
 
![SS_MRP_LayoutTabSm](../../reporting-services/media/ss-mrp-layouttabsm.png)  

С [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)]можно быстро создать мобильные отчеты [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , оптимизированные для мобильных и множества других устройств. Мобильные отчеты содержат различные визуализации, от диаграмм времени, категорий и сравнения до древовидных и пользовательских карт. 

* Подключите мобильные отчеты к различным источникам данных, включая локальные данные SQL Server и Analysis Services. 
* Мобильные отчеты можно составлять в области конструктора, настраивая строки и столбцы сетки и используя гибкие элементы мобильных отчетов, которые масштабируются в соответствии с любым размером экрана. 
* Мобильные отчеты можно сохранять на сервере служб Reporting Services, а затем просматривать в браузере или мобильном приложении Power BI на устройствах iPad, iPhone, телефонах и планшетах Android и на устройствах Windows 10.
  
## <a name="create-includessrsnoversionmdincludesssrsnoversion-mdmd--mobile-reports"></a>Создание мобильных отчетов [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]  
  
Эти статьи помогут вам приступить к работе.
-  Загрузить [издатель мобильных отчетов SQL Server](https://go.microsoft.com/fwlink/?LinkID=733527)  
-  [Создание мобильных отчетов служб Reporting Services](../../reporting-services/mobile-reports/create-a-reporting-services-mobile-report.md)  
-  [End-to-end walkthrough: Create mobile reports and KPIs in SQL Server 2016 Reporting Services](http://christopherfinlan.com/2015/12/21/how-to-create-mobile-reports-and-kpis-in-sql-server-reporting-services-2016-an-end-to-end-walkthrough/) (Пошаговое руководство. Создание мобильных отчетов и определение ключевых показателей эффективности в SQL Server 2016 Reporting Services) (Статья блога Кристофера Финлана (Christopher Finlan))  
- [Design first, or data first](../../reporting-services/mobile-reports/design-first-or-data-first-when-creating-in-reporting-services-mobile-reports.md)(Проектирование отчетов на основе смоделированных или собственных данных). Вы можете выбрать, на основе каких данных будет спроектирован ваш отчет: смоделированных или собственных.  
- [Data for Reporting Services mobile reports](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md)(Данные для мобильных отчетов служб Reporting Services). Используйте данные из общих наборов данных или подготавливайте данные из книг Excel для включения в мобильные отчеты.
- [How data refresh works in mobile reports and KPIs in Reporting Services](http://christopherfinlan.com/2016/02/10/so-refreshinghow-data-refresh-works-with-mobile-reports-and-kpis-in-reporting-services/) (Как происходит обновление данных мобильных отчетов и ключевых показателей эффективности в службах Reporting Services). Запись блога Кристофера Финлана (Christopher Finlan).
- [Добавление визуализаций в мобильные отчеты](../../reporting-services/mobile-reports/add-visualizations-to-reporting-services-mobile-reports.md)
- [Датчики в мобильных отчетах](../../reporting-services/mobile-reports/add-gauges-to-mobile-reports-reporting-services.md)
- [Карты в мобильных отчетах](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)
- [Создание фирменной символики веб-портала и мобильных отчетов](../../reporting-services/branding-the-web-portal.md) с использованием корпоративных цветов и логотипа.
  
## <a name="ssrs-mobile-reports-in-the-power-bi-mobile-apps"></a>Мобильные отчеты SSRS в мобильных приложениях Power BI

-  См. статью [Просмотр ключевых показателей эффективности и мобильных отчетов Reporting Services в мобильных приложениях iOS](https://powerbi.microsoft.com/documentation/powerbi-mobile-iphone-kpis-mobile-reports).
-  См. статью [Просмотр ключевых показателей эффективности и мобильных отчетов Reporting Services в приложении Power BI для устройств Android](https://powerbi.microsoft.com/documentation/powerbi-mobile-android-kpis-mobile-reports).
-  См. статью [Просмотр ключевых показателей эффективности и мобильных отчетов Reporting Services в мобильном приложении Power BI для Windows 10](https://powerbi.microsoft.com/documentation/powerbi-mobile-win10-kpis-mobile-reports/).    

## <a name="see-also"></a>См. также:  
  
-   [Создание, изменение и удаление общих источников данных (SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)  
-   [Управление общими наборами данных](../../reporting-services/report-data/manage-shared-datasets.md)  
-  [Работа с ключевыми показателями эффективности в службах Reporting Services](../../reporting-services/working-with-kpis-in-reporting-services.md)  
- [Enable a report server for Power BI mobile access (Включение доступа к серверу отчетов для мобильного приложения Power BI)](../../reporting-services/report-server/enable-a-report-server-for-power-bi-mobile-access.md)  

  
  

