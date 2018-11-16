---
title: Открытие мобильного отчета с определенными параметрами строки запроса | Документы Майкрософт
ms.date: 10/25/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 4eeb3204-e207-4ac0-aff3-bfc4926e5754
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 090aaf383a80eb0a991f040656f2098965544b35
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51812193"
---
# <a name="open-a-mobile-report-with-specific-query-string-parameters--reporting-services"></a>Открытие мобильного отчета с определенными параметрами строки запроса | Службы Reporting Services
Если у вас есть мобильный отчет [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с параметрами, а также источник данных [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] , можно включить в URL-адрес отчета параметры строки запроса, чтобы он автоматически открывался с заданными значениями. 
1.  Создайте [мобильный отчет с параметрами](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md).

2. Откройте отчет в издателе мобильных отчетов и выберите вкладку "Данные". 

2. Найдите имя набора данных на вкладке в нижней части таблицы и требуемое имя поля. 
    
    ![mobile-report-publisher-parameter-data-view](../../reporting-services/mobile-reports/media/mobile-report-publisher-parameter-data-view.png)
    
2.  Синтаксис URL-адреса зависит от источника данных. 

     **Для источника данных служб SQL Server Analysis Services**. Создайте URL-адрес с параметром строки запроса в следующем формате:

    `https://<servername>/reports/<report-folder-name>/<report-name>?<dataset-name>.<field-name>=<parameter-value>`

    Пример:
    
    `https://sampleserver/reports/adventureworks-reports/adventureworks-load-on-demand?TimeChartLoD.category=Clothing` 
    
     **Для источника данных SQL Server**. Параметр строки запроса почти такой же, но с символом \@ перед именем поля:

    `https://<servername>/reports/<report-folder-name>/<report-name>?<dataset-name>.@<field-name>=<parameter-value>`

    Пример:
    
      `https://sampleserver/reports/adventureworks-reports/adventureworks-load-on-demand?TimeChartLoD.@category=Clothing` 

    
3.  Этот URL-адрес открывает отчет на сервере, автоматически отфильтрованный по указанному значению параметра.

    ![mobile-report-publisher-parameter-web-portal-view](../../reporting-services/mobile-reports/media/mobile-report-publisher-parameter-web-portal-view.png)

### <a name="see-also"></a>См. также раздел

[Добавление параметров в мобильный отчет](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md)

