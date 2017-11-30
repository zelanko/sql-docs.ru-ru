---
title: "Сбор мелких срезов на круговой диаграмме (построитель отчетов и службы SSRS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21c2b8cb-b9ca-4bc0-bf49-50ba432562f6
caps.latest.revision: "10"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a791e5bae17ab1259fb664d065a9a13fcde21aa1
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="collect-small-slices-on-a-pie-chart-report-builder-and-ssrs"></a>Сбор мелких срезов на круговой диаграмме (построитель отчетов и службы SSRS)
Круговые диаграммы со слишком большим количеством срезов могут быть сложны для восприятия. Узнайте, как объединить множество мелких срезов на круговой диаграмме в отчете [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с разбивкой на страницы в один большой срез.
 
 Чтобы собрать мелкие срезы в один, сначала следует решить, как будет измеряться порог для сбора мелких срезов — в процентном отношении от круговой диаграммы или как фиксированное значение. 
 
 Чтобы попробовать сделать это с образцами данных, см. раздел [Учебник. Добавление круговой диаграммы к отчету (построитель отчетов)](Tutorial:%20Add%20a%20Pie%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md), где приводятся пошаговые инструкции по объединению маленьких срезов в один большой.
 
 ![report-builder-pie-chart-other-slice](../../reporting-services/report-design/media/report-builder-pie-chart-other-slice.png)
  
 Можно также собрать мелкие срезы во вторую круговую диаграмму, вызываемую из собранного среза первой диаграммы. Вторая круговая диаграмма отображается справа от исходной круговой диаграммы.  
  
 Нельзя объединить в один срез срезы воронкообразных и пирамидальных диаграмм.  
  
 
## <a name="to-collect-small-slices-into-a-single-slice-on-a-pie-chart"></a>Сбор мелких срезов в один срез круговой диаграммы  
  
1.  Откройте панель «Свойства».  
  
2.  В области конструктора щелкните любой сегмент круговой диаграммы. На панели «Свойства» отображаются свойства ряда.  
  
3.  В разделе **Общие** разверните узел **CustomAttributes** .  
  
4.  Присвойте свойству CollectedStyle значение **SingleSlice**.  

    ![report-builder-pie-chart-single-slice-property](../../reporting-services/media/report-builder-pie-chart-single-slice-property.png)
  
5.  Задайте значение порога сбора и его тип. Следующие примеры демонстрируют общие способы задания порогов сбора.  
  
    -   **В процентах.** Например, можно собрать в один срез все срезы круговой диаграммы, не превышающие 10%.  
  
         Присвойте свойству CollectedThresholdUsePercent значение **True**.  
  
         Присвойте свойству CollectedThreshold значение **10**.  
  
        > [!NOTE]  
        >  Если присвоить свойству CollectedStyle значение **SingleSlice**, свойству CollectedThreshold — значение больше **100**, а свойству CollectedThresholdUsePercent — значение **True**, для диаграммы будет создано исключение из-за невозможности вычислить процентную величину. Чтобы избежать этого, присвойте свойству CollectedThreshold значение меньше **100**.  
  
    -   **По значению данных.** Например, можно собрать в один срез все срезы круговой диаграммы, не превышающие 5000%.  
  
         Присвойте свойству CollectedThresholdUsePercent значение **False**.  
  
         Присвойте свойству CollectedThreshold значение **5000**.  
  
6.  Задайте в качестве свойства CollectedLabel строку, представляющую текстовую метку, которая будет отображена на собранном срезе.  
  
7.  (Необязательно) Присвойте значения свойствам CollectedSliceExploded, CollectedColor, CollectedLegendText и CollectedToolTip. Эти свойства определяют внешний вид, цвет, текстовую метку, текст условных обозначений и подсказку отдельного среза.  
  
## <a name="to-collect-small-slices-into-a-secondary-callout-pie-chart"></a>Сбор мелких срезов во вторичную, вызываемую круговую диаграмму  
  
1.  Выполните приведенные выше шаги 1—3.  
  
2.  Присвойте свойству CollectedStyle значение **CollectedPie**.  
  
3.  Определите для свойства CollectedThresholdproperty значение порога, мелкие срезы со значениями ниже которого будут собираться в один срез. Если свойству CollectedStyle задать значение **CollectedPie**, свойство CollectedThresholdUsePercentproperty всегда будет иметь значение **True**, а пороговое значение для сбора будет всегда измеряться в процентах.  
  
4.  (Необязательно) Присвойте значения свойствам CollectedColor, CollectedLabel, CollectedLegendText и CollectedToolTip. Все остальные свойства, в имя которых входит «Collected», не относятся к собранной диаграмме.  
  
> [!NOTE]  
>  Поскольку вторичная круговая диаграмма вычисляется на основе мелких срезов данных, она появится только в режиме предварительного просмотра. Она не появляется в области конструктора.  
  
> [!NOTE]  
>  Форматировать вторичную круговую диаграмму нельзя. По этой причине настоятельно рекомендуется пользоваться для сбора мелких срезов круговых диаграмм первым методом.  
  
## <a name="see-also"></a>См. также:  
* [Учебник. Добавление круговой диаграммы к отчету (построитель отчетов)](Tutorial:%20Add%20a%20Pie%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md)
*  [Круговые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
*  [Форматирование точек данных на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
*  [Отображение меток точек данных за пределами круговой диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
*  [Отображение процентных значений на круговой диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)     
  
