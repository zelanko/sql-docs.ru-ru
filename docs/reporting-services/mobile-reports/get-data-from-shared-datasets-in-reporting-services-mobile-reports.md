---
title: Получение данных из общих наборов данных в мобильных отчетах служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: mobile-reports
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0b846451-c8d0-412c-802d-a42bb1ff8c63
caps.latest.revision: 18
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb83dd013101b14ad45da1fb9ef091dcbea727d1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33018399"
---
# <a name="get-data-from-shared-datasets-in-reporting-services-mobile-reports"></a>Get data from shared datasets in Reporting Services mobile reports
Помимо [загрузки данных из файлов Excel](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md), издатель мобильных отчетов для SQL Server также может получать доступ к данным практически из любого источника. Для доступа к данным требуется общий источник данных, настроенный на веб-портале служб Reporting Services. Узнайте больше о [создании общих источников данных](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md) и [создании общих наборов данных](../../reporting-services/report-data/manage-shared-datasets.md).  
  
После того как общие источники данных и общие наборы данных настроены на сервере служб Reporting Services, вы можете использовать их в мобильных отчетах, создаваемых в [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)].   
  
После того, как установлено подключение к серверу [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] из [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)], соединение мобильного отчета с общим набором данных является простым процессом.   
  
1. На вкладке **Данные** выберите **Добавление данных**.  
  
2. Выберите **Сервер отчетов**.   
  
3.  Если это первое подключение к серверу, введите имя сервера, а также свое имя и пароль. Укажите имя сервера в поле "Адрес сервера" в следующем формате:  
  
    \<"имя_сервера">/reports/  
  
    В данном примере:  
       
    ![SSMRP_ConnectToServer](../../reporting-services/mobile-reports/media/ssmrp-connecttoserver.png)  
      
  
4. При выборе сервера [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] вы увидите доступные наборы данных в папках. Выберите набор данных, чтобы импортировать данные в [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)].  
  
   ![SS_MRP_ServerData](../../reporting-services/mobile-reports/media/ss-mrp-serverdata.png)  
  
После импорта набора данных можно создать свой мобильный отчет таким же образом, как при использовании смоделированных данных или локальных данных из файла Excel.  
  
По умолчанию, общий набор данных всегда содержит самые актуальные данные, так как при каждом просмотре мобильного отчета, основанного на этом наборе данных, SQL Server выполняет базовый запрос и возвращает самые актуальные данные. Конечно, если ваш мобильный отчет просматривает большое число пользователей, это может быть не лучшим вариантом, поэтому вы можете настроить кэш на периодическое выполнение запроса и кэширование получаемого в результате набора данных. Эта статья в блоге описывает, [как кэширование и обновление данных работают на веб-портале](http://christopherfinlan.com/2016/02/10/so-refreshinghow-data-refresh-works-with-mobile-reports-and-kpis-in-reporting-services/).  
  
## <a name="add-edit-or-remove-a-report-server"></a>Добавление, изменение или удаление сервера отчетов  
  
Если вы уже подключились к серверу отчетов, при выборе параметра **Добавить данные** на вкладке "Данные" вы не сможете добавить другой сервер отчетов. Выполните следующие действия.  
  
1. В верхнем левом углу щелкните **Соединения**.  
  
   ![SSMRP_AddConnectionIcon](../../reporting-services/mobile-reports/media/ssmrp-addconnectionicon.png)  
     
   Справа откроется область "Соединение с сервером".  
     
   ![SSMRP_ServerConnectnPane](../../reporting-services/mobile-reports/media/ssmrp-serverconnectnpane.png)  
     
2. Добавить новое подключение к серверу либо измените или удалите существующие подключения.  
  
### <a name="see-also"></a>См. также раздел  
- [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-  [Веб-портал (собственный режим служб SSRS)](../../reporting-services/web-portal-ssrs-native-mode.md)  
-  См. статью [Просмотр мобильных отчетов SQL Server и ключевых показателей эффективности в приложении для iPad](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  (Power BI для iOS).  
-  См. статью [Просмотр мобильных отчетов SQL Server и ключевых показателей эффективности в приложении для iPhone](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Power BI для iOS).  
  
  
  
  

