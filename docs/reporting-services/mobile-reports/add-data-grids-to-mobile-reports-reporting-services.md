---
title: "Добавление сеток данных в мобильные отчеты | Службы Reporting Services | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: mobile-reports
ms.reviewer: 
ms.suite: pro-bi
ms.technology: reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe98a970-90d3-44d1-9189-9141c237f141
caps.latest.revision: "4"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5297f37049305d971cc5f97d0f34c65002272061
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="add-data-grids-to-mobile-reports--reporting-services"></a>Добавление сеток данных в мобильные отчеты | Службы Reporting Services
Иногда лучшая визуализация — это сами данные. Рассмотрим три вида *сеток данных*(или таблиц) для отображения данных в [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)]:
* Простая сетка данных
* Сетка данных индикатора
* Сетка данных диаграммы

## <a name="simple-data-grid"></a>Простая сетка данных
Самая основная, простая сетка данных позволяет отобразить несколько столбцов данных, выбрав нужное форматирование и заголовки. 

![mobile-report-simple-data-grid](../../reporting-services/mobile-reports/media/mobile-report-simple-data-grid.png)

Добавив сетку данных в область конструктора, можно подключить ее к фактическим данным.

1. Перетащите простую сетку данных с вкладки **Макет** на сетку конструктора и задайте ей нужный размер.

2. Получите [данные из Excel или общего набора данных](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md).

3. Откройте вкладку **Данные** , а затем в области **Свойства данных** в разделе **Данные для представления сетки** выберите таблицу данных.

4. В области **Столбцы** выберите нужные столбцы. Отсортируйте их, переименуйте и задайте формат и способ агрегирования. 

 
##  <a name="indicator-data-grid"></a>Сетка данных индикатора
В сетку данных индикатора можно добавлять столбцы с датчиками.

![mobile-report-indicator-data-grid](../../reporting-services/mobile-reports/media/mobile-report-indicator-data-grid.png)

1. Перетащите сетку данных индикаторы с вкладки **Макет** на сетку конструктора и задайте ей нужный размер.

2. На вкладке **Данные** в области **Столбцы** выберите пункт **Добавить столбец датчика**. 

3. Выберите **Параметры**, а затем **Тип датчика**. 

4. Настройте поля **Значение** , **Сравнение** и **Направление значения**как для [датчиков, добавляемых в мобильный отчет напрямую](../../reporting-services/mobile-reports/add-gauges-to-mobile-reports-reporting-services.md).

Сетка данных будет автоматически передавать датчику только те данные, которые относятся к этой строке сетки данных.  

## <a name="chart-data-grid"></a>Сетка данных диаграммы
В сетку данных диаграммы можно добавлять столбцы с датчиками или диаграммами. 

![mobile-report-chart-data-grid](../../reporting-services/mobile-reports/media/mobile-report-chart-data-grid.png)

При добавлении столбца диаграммы в сетку данных необходимо добавить отдельную таблицу данных, каждая строка которой будет содержать данные для диаграммы. Вторая таблица должна иметь общее поле с основной таблицей данных, так чтобы каждая ее строка была связана с соответствующими данными диаграммы. 

1. Перетащите сетку данных диаграммы с вкладки **Макет** на сетку конструктора и задайте ей нужный размер.

2. На вкладке **Данные** в области **Столбцы** выберите пункт **Добавить столбец диаграммы**. 

3. Получите [данные из Excel или общего набора данных](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md) , чтобы добавить вторую таблицу данных, имеющую общее поле с основной таблицей данных (если это еще не сделано).

4. В разделе **Свойства данных**выберите основную таблицу данных в поле **Данные для представления сетки**, а вторую таблицу — в поле **Эталонные данные для визуализаций диаграмм**.

5. Выберите **Параметры**, а затем **Тип диаграммы**.
 
6. Выберите **Поле данных диаграммы**, **Поиск по источнику**и **Поиск по месту назначения**. 
   Эти три свойства определяют, каким образом сетка данных должна предоставлять данные для каждой диаграммы в столбце.
   
   *   **Поиск по источнику** — это поле в таблице данных, выбранной в поле **Данные для представления сетки**. Это поле действует как построчный фильтр, который применяется к эталонной таблице данных для передачи данных по каждой строке во встроенную диаграмму. 
   * **Поиск по месту назначения** — это поле в таблице данных, выбранной в поле **Эталонные данные для визуализаций диаграмм**. Данные для диаграммы в каждой строке будут связаны по этим двум полям.   
   * **Поле "Данные диаграммы"** определяет, какой показатель в таблице **Эталонные данные для визуализаций диаграмм** будет использоваться как значение по оси y или ряд на диаграмме в каждой строке.  

## <a name="see-also"></a>См. также: 
* [Maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)
* [Navigators in Reporting Services mobile reports (Навигаторы в мобильных отчетах служб Reporting Services)](../../reporting-services/mobile-reports/add-navigators-to-reporting-services-mobile-reports.md)
* [Visualizations in Reporting Services mobile reports (Визуализации в мобильных отчетах служб Reporting Services)](../../reporting-services/mobile-reports/add-visualizations-to-reporting-services-mobile-reports.md)
* [Gauges in Reporting Services mobile reports (Датчики в мобильных отчетах служб Reporting Services)](../../reporting-services/mobile-reports/add-gauges-to-mobile-reports-reporting-services.md)  
 
  
