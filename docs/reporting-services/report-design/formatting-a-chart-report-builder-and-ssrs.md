---
title: "Форматирование диаграммы (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- "10214"
- sql13.rtp.rptdesigner.charttitleproperties.shadow.f1
- sql13.rtp.rptdesigner.serieslabelproperties.font.f1
- "10149"
- sql13.rtp.rptdesigner.legendproperties.fill.f1
- sql13.rtp.rptdesigner.seriesproperties.shadow.f1
- "10255"
- sql13.rtp.rptdesigner.seriesproperties.fill.f1
- "10154"
- "10170"
- "10173"
- "10169"
- "10158"
- sql13.rtp.rptdesigner.minorgridlineproperties.gridlineoptions.f1
- sql13.rtp.rptdesigner.calculatedseriesproperties.borders.f1
- "10246"
- sql13.rtp.rptdesigner.serieslabelproperties.fill.f1
- "10150"
- sql13.rtp.rptdesigner.majorgridlineproperties.gridlineoptions.f1
- "10159"
- sql13.rtp.rptdesigner.chartproperties.fill.f1
- "10160"
- "10182"
- "10163"
- sql13.rtp.rptdesigner.charttitleproperties.fill.f1
- "10164"
- "10253"
- "10216"
- "10171"
- "10257"
- sql13.rtp.rptdesigner.chartareaproperties.shadow.f1
- sql13.rtp.rptdesigner.chartareaproperties.fill.f1
- sql13.rtp.rptdesigner.calculatedseriesproperties.fill.f1
- sql13.rtp.rptdesigner.charttitleproperties.font.f1
- sql13.rtp.rptdesigner.seriesproperties.markers.f1
- sql13.rtp.rptdesigner.calculatedseriesproperties.shadow.f1
- sql13.rtp.rptdesigner.charttitleproperties.borders.f1
- sql13.rtp.rptdesigner.chartareaproperties.border.f1
- sql13.rtp.rptdesigner.chartproperties.border.f1
- "10247"
ms.assetid: d3984300-c766-42f8-b7c4-863123d67c99
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fc669d43fc5331a1ce161b0c1c2098a38c5224fb
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="formatting-a-chart-report-builder-and-ssrs"></a>Форматирование диаграммы (построитель отчетов и службы SSRS)
  После определения данных для диаграммы и нужного представления диаграммы можно добавить форматирование, чтобы улучшить общий внешний вид и выделить ключевые точки данных. Наиболее общие параметры форматирования могут быть изменены в диалоговом окне «Свойства». Для этого нужно щелкнуть правой кнопкой мыши элемент диаграммы, чтобы отобразить контекстное меню. Каждый элемент диаграммы имеет собственное диалоговое окно. Дополнительные сведения о элементах диаграмм см. в статье [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md).  
  
 Все свойства, связанные с диаграммой, расположены на панели «Свойства», но многие из этих свойств можно также задать в диалоговом окне. При форматировании ряда можно указать характерные для ряда свойства с помощью пользовательских атрибутов, которые можно найти только в категории свойств **CustomAttributes** , расположенной на панели "Свойства".  
  
 Для эффективного форматирования диаграммы с помощью минимального числа шагов измените стиль границ по умолчанию, палитру и стиль отображения. Эти три характеристики оказывают самое большое влияние на зрительное восприятие диаграммы. Стили отображения применимы только к круговым, кольцевым, столбчатым диаграммам и гистограммам.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a>В этом разделе  
 [Форматирование цветов для рядов на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)  
 Рассматривается определение цветов с помощью палитры, определение собственной палитры и определение цветов на основе выражения.  
  
 [Форматирование меток оси на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)  
 Рассматривается отображение линий сетки, делений и заголовков, а также форматирование чисел и дат на шкале оси.  
  
 [Форматирование условных обозначений на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)  
 Рассматривается изменение расположения и форматирование элементов в условных обозначениях диаграммы.  
  
 [Форматирование точек данных на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
 Рассматривается размещение меток точек данных и форматирование маркеров точек данных для каждого ряда диаграммы.  
  
 [Эффекты рельефа, объемные и другие эффекты в диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/chart-effects-3d-bevel-and-other-report-builder.md)  
 Рассматриваются различные объемные эффекты, которые можно применить к диаграмме.  
  
 [Добавление границы рамки в диаграмму (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)  
 Объясняет, как добавить к диаграмме границу рамки.  
  
## <a name="see-also"></a>См. также  
 [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Добавление границы рамки в диаграмму (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)   
 [Задание цветов диаграммы с помощью палитры (построитель отчетов и службы SSRS)](../../reporting-services/report-design/define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)   
 [Добавление в диаграмму стилей рельефа, приподнятости и текстуры (построитель отчетов и службы SSRS)](../../reporting-services/report-design/chart-effects-add-bevel-emboss-or-texture-report-builder.md)  
  
  
