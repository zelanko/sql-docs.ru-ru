---
title: "Группирование данных в мобильном отчете по столбцам или строкам | Службы Reporting Services | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9ebd36c-a337-47ae-83e5-6c2f2144eb52
caps.latest.revision: "6"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: de6eddf3b9338ac15f5036c2065df2f82f0c9bab
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="group-data-by-columns-or-rows-in-a-mobile-report--reporting-services"></a>Группирование данных в мобильном отчете по столбцам или строкам | Службы Reporting Services
Во многих типах диаграмм в [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)]данные можно группировать по столбцам или строкам. Для этого выполните описанные ниже действия.

Данные во временных, круговых и воронкообразных диаграммах можно группировать по строкам и по столбцам. 
* Группирование по столбцам пригодится, если таблица содержит несколько столбцов, данные в которых необходимо сравнить. 
* Группирование по строкам больше подойдет в случае, если один столбец в таблице содержит имена различных категорий. 

В описанных ниже действиях для демонстрации различий в группировании данных по строкам и по столбцам диаграммы используется сравнительная таблица итогов с данными, смоделированными в [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] .  

1. Перетащите **сравнительную таблицу итогов** с вкладки **Макет** в область конструктора и увеличьте ее размер.

2. Выберите вкладку **Данные** . Вы увидите таблицу SimulatedTable с рядом столбцов: от **Метрика1** до **Метрика5** и от **Сравнение1** до **Сравнение5**. 

   ![mobile-report-data-group-column](../../reporting-services/mobile-reports/media/mobile-report-data-group-column.png)

3. В области **Свойства данных** в поле **Основной ряд** выбран вариант **SimulatedTable**. Щелкните стрелку в поле рядом с полем **Основной ряд**и вы увидите, что выбраны параметры **Метрика1** — **Метрика5** .

   ![mobile-report-properties-columns](../../reporting-services/mobile-reports/media/mobile-report-properties-columns.png)

   Для поля **Ряд сравнения** выбраны параметры **Сравнение1** -- **Сравнение5**.
   
4. Выберите **Предварительный просмотр**.

   ![mobile-report-chart-by-columns](../../reporting-services/mobile-reports/media/mobile-report-chart-by-columns.png)

   Каждая полоска в диаграмме представляет один из столбцов в таблице. Более толстые полоски соответствуют столбцам Metric, а более тонкие — столбцам Comparison.

5. Щелкните стрелку назад в левом верхнем углу, чтобы выйти из режима предварительного просмотра.

6. На вкладке **Макет** в области **Свойства визуальных элементов** изменение значение **По столбцам** в поле **Структура данных** на значение **По строкам**.  

7. Выберите вкладку **Данные** . Теперь в таблице SimulatedTable наряду со столбцами **Метрика** и **Сравнение** отображается столбец **Категория**, содержащий категории от А до E. 

   ![mobile-report-data-group-rows](../../reporting-services/mobile-reports/media/mobile-report-data-group-rows.png)

8.  В области **Свойства данных** появляется поле "Столбец категории", в котором перечислены строки столбца "Категория" в таблице SimulatedTable. В поле "Основной ряд" выберите столбец, из которого будут браться значения. По умолчанию [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] выбирает для основного ряда столбцы от "Метрика1" до "Метрика5", а для ряда сравнения — столбцы от "Сравнение1" до "Сравнение5". 

    ![mobile-report-properties-rows](../../reporting-services/mobile-reports/media/mobile-report-properties-rows.png)

9. Выберите **Предварительный просмотр**.

   ![mobile-report-chart-by-rows](../../reporting-services/mobile-reports/media/mobile-report-chart-by-rows.png)

   Теперь каждый столбец в диаграмме представляет значения по каждой категории в столбце "Категория".

### <a name="see-also"></a>См. также:
* [Visualizations in Reporting Services mobile reports (Визуализации в мобильных отчетах служб Reporting Services)](../../reporting-services/mobile-reports/add-visualizations-to-reporting-services-mobile-reports.md)
