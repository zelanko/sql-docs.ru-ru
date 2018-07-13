---
title: Форматирование диаграммы (построитель отчетов и службы SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10214"
- sql12.rtp.rptdesigner.calculatedseriesproperties.fill.f1
- sql12.rtp.rptdesigner.serieslabelproperties.fill.f1
- sql12.rtp.rptdesigner.legendproperties.fill.f1
- "10149"
- sql12.rtp.rptdesigner.seriesproperties.shadow.f1
- sql12.rtp.rptdesigner.seriesproperties.markers.f1
- "10255"
- sql12.rtp.rptdesigner.charttitleproperties.fill.f1
- "10154"
- "10170"
- "10173"
- sql12.rtp.rptdesigner.seriesproperties.fill.f1
- "10169"
- "10158"
- sql12.rtp.rptdesigner.chartareaproperties.fill.f1
- sql12.rtp.rptdesigner.charttitleproperties.shadow.f1
- "10246"
- "10150"
- sql12.rtp.rptdesigner.calculatedseriesproperties.borders.f1
- sql12.rtp.rptdesigner.chartproperties.fill.f1
- "10159"
- sql12.rtp.rptdesigner.majorgridlineproperties.gridlineoptions.f1
- "10160"
- sql12.rtp.rptdesigner.serieslabelproperties.font.f1
- "10182"
- "10163"
- "10164"
- "10253"
- "10216"
- "10171"
- "10257"
- sql12.rtp.rptdesigner.chartareaproperties.border.f1
- sql12.rtp.rptdesigner.calculatedseriesproperties.shadow.f1
- sql12.rtp.rptdesigner.chartproperties.border.f1
- sql12.rtp.rptdesigner.minorgridlineproperties.gridlineoptions.f1
- sql12.rtp.rptdesigner.chartareaproperties.shadow.f1
- sql12.rtp.rptdesigner.charttitleproperties.borders.f1
- sql12.rtp.rptdesigner.charttitleproperties.font.f1
- "10247"
ms.assetid: d3984300-c766-42f8-b7c4-863123d67c99
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 9187661ada5df23435dae83122ce8f14a4a5c609
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183823"
---
# <a name="formatting-a-chart-report-builder-and-ssrs"></a>Форматирование диаграммы (построитель отчетов и службы SSRS)
  После определения данных для диаграммы и нужного представления диаграммы можно добавить форматирование, чтобы улучшить общий внешний вид и выделить ключевые точки данных. Наиболее общие параметры форматирования могут быть изменены в диалоговом окне «Свойства». Для этого нужно щелкнуть правой кнопкой мыши элемент диаграммы, чтобы отобразить контекстное меню. Каждый элемент диаграммы имеет собственное диалоговое окно. Дополнительные сведения о элементах диаграмм см. в статье [Диаграммы (построитель отчетов и службы SSRS)](charts-report-builder-and-ssrs.md).  
  
 Все свойства, связанные с диаграммой, расположены на панели «Свойства», но многие из этих свойств можно также задать в диалоговом окне. При форматировании ряда можно указать характерные для ряда свойства с помощью пользовательских атрибутов, которые можно найти только в категории свойств **CustomAttributes** , расположенной на панели "Свойства".  
  
 Для эффективного форматирования диаграммы с помощью минимального числа шагов измените стиль границ по умолчанию, палитру и стиль отображения. Эти три характеристики оказывают самое большое влияние на зрительное восприятие диаграммы. Стили отображения применимы только к круговым, кольцевым, столбчатым диаграммам и гистограммам.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a>в этом разделе  
 [Форматирование цветов для рядов на диаграмме (построитель отчетов и службы SSRS)](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)  
 Рассматривается определение цветов с помощью палитры, определение собственной палитры и определение цветов на основе выражения.  
  
 [Форматирование меток оси на диаграмме (построитель отчетов и службы SSRS)](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)  
 Рассматривается отображение линий сетки, делений и заголовков, а также форматирование чисел и дат на шкале оси.  
  
 [Форматирование условных обозначений на диаграмме (построитель отчетов и службы SSRS)](chart-legend-formatting-report-builder.md)  
 Рассматривается изменение расположения и форматирование элементов в условных обозначениях диаграммы.  
  
 [Форматирование точек данных на диаграмме (построитель отчетов и службы SSRS)](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
 Рассматривается размещение меток точек данных и форматирование маркеров точек данных для каждого ряда диаграммы.  
  
 [Эффекты рельефа, объемные и другие эффекты в диаграмме (построитель отчетов и службы SSRS)](chart-effects-3d-bevel-and-other-report-builder.md)  
 Рассматриваются различные объемные эффекты, которые можно применить к диаграмме.  
  
 [Добавление границы рамки в диаграмму (построитель отчетов и службы SSRS)](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)  
 Объясняет, как добавить к диаграмме границу рамки.  
  
## <a name="see-also"></a>См. также  
 [Диаграммы (построитель отчетов и службы SSRS)](charts-report-builder-and-ssrs.md)   
 [Добавление границы рамки в диаграмму &#40;построитель отчетов и службы SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)   
 [Задание цветов диаграммы с помощью палитры &#40;построитель отчетов и службы SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)   
 [Добавление в диаграмму стилей рельефа, приподнятости и текстуры &#40;построитель отчетов и службы SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md)  
  
  
