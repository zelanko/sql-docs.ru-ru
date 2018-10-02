---
title: Отображение процентных значений на круговой диаграмме (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 721899b9a6f8dd8eff70b269ebae7867d6c3d587
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47790432"
---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a>Отображение процентных значений на круговой диаграмме (построитель отчетов и службы SSRS)
В отчетах [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с разбиением на страницы по умолчанию в условных обозначениях отображаются категории. Вы также можете добавить процентные значения в условные обозначения или на сами срезы круговой диаграммы.   

![report-builder-pie-chart-preview-percents](../../reporting-services/media/report-builder-pie-chart-preview-percents.png)

 Чтобы попробовать сделать это с образцами данных, см. раздел [Учебник. Добавление круговой диаграммы к отчету (построитель отчетов)](Tutorial:%20Add%20a%20Pie%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md), где приводятся инструкции по добавлению процентных значений в срезы круговой диаграммы.
 
  
## <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a>Отображение на круговой диаграмме значений в процентах в качестве меток  
  
1.  Добавьте в отчет круговую диаграмму. Дополнительные сведения см. в разделе [Добавление диаграммы в отчет (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md).  
  
2.  В области конструктора щелкните правой кнопкой мыши круговую диаграмму и выберите пункт **Отобразить метки данных**. Метки данных должны появиться в каждом срезе круговой диаграммы.  
  
3.  В области конструктора щелкните правой кнопкой мыши метки и выберите пункт **Свойства метки ряда**. Появится диалоговое окно **Свойства метки ряда** .  
  
4.  Присвойте параметру **Данные метки** значение **#PERCENT** .  
  
5.  (Необязательно) Чтобы указать для метки количество десятичных разрядов, введите значение #PERCENT{P*n*}, где *n* — число десятичных разрядов. Например, чтобы не отображать десятичные разряды, введите «#PERCENT{P0}».  
  
## <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a>Отображение в условных обозначениях круговой диаграммы значений в процентах  
  
1.  В области конструктора щелкните правой кнопкой мыши круговую диаграмму и выберите пункт **Свойства ряда**. Откроется диалоговое окно **Свойства ряда** .  
  
2.  На вкладке **Условные обозначения**для свойства **Пользовательский текст условных обозначений** введите значение **#PERCENT** .  
  
## <a name="see-also"></a>См. также:  
* [Учебник. Добавление круговой диаграммы к отчету (построитель отчетов)](Tutorial:%20Add%20a%20Pie%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md)
*  [Круговые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
*  [Форматирование условных обозначений на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
*  [Отображение меток точек данных за пределами круговой диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 
  
