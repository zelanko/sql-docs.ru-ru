---
title: "Отображение процентных значений на круговой диаграмме (построитель отчетов и службы SSRS) | Документы Microsoft"
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
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6c0fdf9d1b694f2f6d49389e913d1c156ba77838
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a>Отображение процентных значений на круговой диаграмме (построитель отчетов и службы SSRS)
В [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] разбиением на страницы, по умолчанию условные обозначения отображаются категории. Вы также можете проценты в условных обозначениях или сами круговой диаграммы.   

![report-builder-pie-chart-preview-percents](../../reporting-services/media/report-builder-pie-chart-preview-percents.png)

 [Учебника: Добавление круговой диаграммы в отчет (построитель отчетов)](Tutorial:%20Add%20a%20Pie%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md) поможет выполнить добавление процентных показателей для секторов круговой диаграммы, если вы хотите сделать это с образцами данных.
 
  
## <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a>Отображение на круговой диаграмме значений в процентах в качестве меток  
  
1.  Добавьте в отчет круговую диаграмму. Дополнительные сведения см. в разделе [Добавление диаграммы в отчет (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md).  
  
2.  В области конструктора щелкните правой кнопкой мыши круговую диаграмму и выберите пункт **Отобразить метки данных**. Метки данных должны появиться в каждом срезе круговой диаграммы.  
  
3.  В области конструктора щелкните правой кнопкой мыши метки и выберите пункт **Свойства метки ряда**. Появится диалоговое окно **Свойства метки ряда** .  
  
4.  Присвойте параметру **Данные метки** значение **#PERCENT** .  
  
5.  (Необязательно) Чтобы указать, сколько метки десятичных разрядов, введите «#PERCENT {P*n*}» где  *n*  число десятичных разрядов. Например, чтобы не отображать десятичные разряды, введите «#PERCENT{P0}».  
  
## <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a>Отображение в условных обозначениях круговой диаграммы значений в процентах  
  
1.  В области конструктора щелкните правой кнопкой мыши круговую диаграмму и выберите пункт **Свойства ряда**. Откроется диалоговое окно **Свойства ряда** .  
  
2.  На вкладке **Условные обозначения**для свойства **Пользовательский текст условных обозначений** введите значение **#PERCENT** .  
  
## <a name="see-also"></a>См. также:  
* [Учебник: Добавление круговой диаграммы к отчету (построитель отчетов)](Tutorial:%20Add%20a%20Pie%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md)
*  [Круговые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
*  [Форматирование условных обозначений на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
*  [Отображение меток точек данных за пределами круговой диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 
  
