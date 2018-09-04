---
title: Открытие мобильного отчета с определенными параметрами строки запроса | Документы Майкрософт
ms.date: 10/25/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.suite: pro-bi
ms.topic: conceptual
ms.assetid: 4eeb3204-e207-4ac0-aff3-bfc4926e5754
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5096f18bbb2ce1be88d6ad7bbf9e0684dcb04103
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43282756"
---
# <a name="open-a-mobile-report-with-specific-query-string-parameters--reporting-services"></a>Открытие мобильного отчета с определенными параметрами строки запроса | Службы Reporting Services
Если у вас есть мобильный отчет [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с параметрами, а также источник данных [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] , можно включить в URL-адрес отчета параметры строки запроса, чтобы он автоматически открывался с заданными значениями. 
1.  Создайте [мобильный отчет с параметрами](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md).

2. Откройте отчет в издателе мобильных отчетов и выберите вкладку "Данные". 

2. Найдите имя набора данных на вкладке в нижней части таблицы и требуемое имя поля. 
    
    ![mobile-report-publisher-parameter-data-view](../../reporting-services/mobile-reports/media/mobile-report-publisher-parameter-data-view.png)
    
2.  Синтаксис URL-адреса зависит от источника данных. 

     **Для источника данных служб SQL Server Analysis Services**. Создайте URL-адрес с параметром строки запроса в следующем формате:

    `http://<servername>/reports/<report-folder-name>/<report-name>?<dataset-name>.<field-name>=<parameter-value>`

    Пример:
    
    `http://sampleserver/reports/adventureworks-reports/adventureworks-load-on-demand?TimeChartLoD.category=Clothing` 
    
     **Для источника данных SQL Server**. Параметр строки запроса почти такой же, но с символом \@ перед именем поля:

    `http://<servername>/reports/<report-folder-name>/<report-name>?<dataset-name>.@<field-name>=<parameter-value>`

    Пример:
    
      `http://sampleserver/reports/adventureworks-reports/adventureworks-load-on-demand?TimeChartLoD.@category=Clothing` 

    
3.  Этот URL-адрес открывает отчет на сервере, автоматически отфильтрованный по указанному значению параметра.

    ![mobile-report-publisher-parameter-web-portal-view](../../reporting-services/mobile-reports/media/mobile-report-publisher-parameter-web-portal-view.png)

### <a name="see-also"></a>См. также раздел

[Добавление параметров в мобильный отчет](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md)

