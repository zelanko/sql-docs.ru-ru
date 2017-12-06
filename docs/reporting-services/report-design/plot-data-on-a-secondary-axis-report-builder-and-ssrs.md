---
title: "Построение данных на вспомогательной оси (построитель отчетов и службы SSRS) | Документы Майкрософт"
ms.custom: 
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
caps.latest.revision: "9"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 0a8ae605186909bf5f4423e3a707f3662f267cf1
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="plot-data-on-a-secondary-axis-report-builder-and-ssrs"></a>Построение данных на вспомогательной оси (построитель отчетов и службы SSRS)

Диаграмма имеет оси двух типов: основную и вспомогательную. Вспомогательная ось полезна при сравнении двух наборов значений с двумя различающимися диапазонами данных с общей категорией.  
  
 Например, предположим, что имеется диаграмма, вычисляющая доходы за 2008 год в зависимости от налогов. В этом случае период времени в течение 2008 года является общим для обоих наборов данных. Однако, если оба ряда построить на одной оси Y, нельзя сделать полезное сравнение, т. к. шкала оси Y оптимизирована для самых больших значений в наборе данных. Если показать доход на первичной оси, а налог на вторичной, можно отобразить каждый ряд на своей собственной оси Y со своей собственной шкалой значений. Ряды продолжают использовать общую ось X.  
  
 Если сравнивается более двух рядов, необходимо использовать другой подход для сравнения и отображения на диаграмме нескольких рядов. Дополнительные сведения см. в разделе [Несколько рядов на диаграмме](../../reporting-services/report-design/multiple-series-on-a-chart-report-builder-and-ssrs.md).  
  
 Пример этой диаграммы доступен в виде образца отчета. Дополнительные сведения о скачивании этого и других образцов отчетов см. в статье [(Примеры отчетов построителя отчетов и конструктора отчетов)](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-plot-a-series-on-the-secondary-axis"></a>Построение ряда на вторичной оси  
  
1.  Щелкните правой кнопкой мыши ряды в диаграмме или поле в области **Значения** , которую нужно отобразить на вспомогательной оси, и выберите пункт **Свойства ряда**. Откроется диалоговое окно **Свойства ряда** .  
  
2.  Перейдите на вкладку **Оси и область диаграммы**и выберите, какую из вторичных осей необходимо включить: ось значений или ось категорий.  

## <a name="next-steps"></a>Следующие шаги

[Форматирование меток оси на диаграмме](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
[Указание интервала оси](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
