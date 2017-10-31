---
title: "Добавление пустых точек на диаграмму (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b056119-439f-494f-83cf-ee0c05dc6487
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: acc67d54c387097785317456b70a5936abf05d43
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="add-empty-points-to-a-chart-report-builder-and-ssrs"></a>Add Empty Points to a Chart (Report Builder and SSRS)
Значения NULL отображаются на диаграмме в виде пустых мест или промежутков между точками данных в ряде. В отчетах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с разбиением на страницы пустые точки представляют собой точки данных, которые можно вставить в пустые места, созданные значениями NULL.  
  
 По умолчанию пустые точки вычисляются как среднее значение предыдущей и последующей точек данных, содержащих значения. Это поведение можно изменить, чтобы вместо пустых точек вставлялись значения нуля.  
  
 Дополнительные сведения см. в разделе [Точки данных со значением NULL и пустые точки в диаграммах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-specify-empty-points-on-a-chart"></a>Указание пустых точек на диаграмме  
  
1.  Откройте панель «Свойства».  
  
2.  В области конструктора щелкните правой кнопкой мыши ряд, содержащий значения NULL. На панели «Свойства» отображаются свойства ряда.  
  
3.  Разверните узел **EmptyPoint** .  
  
4.  Укажите значение цвета для свойства Color.  
  
5.  В узле **EmptyPoint** разверните узел «Маркер».  
  
6.  Выберите тип маркера для свойства MarkerType.  
  
    > [!NOTE]  
    >  Тип маркера необходимо выбрать, чтобы добавить пустые точки на гистограмму, столбчатую или точечную диаграмму. Однако для диаграммы с областями, линейчатой и лепестковой диаграммы выбор типа маркера необязателен, поскольку для заполнения пустого пространства или промежутка на этих диаграммах маркер не нужен.  
  
7.  Задайте значение пустой точки.  
  
    1.  На панели «Свойства» разверните узел **CustomAttributes** .  
  
    2.  Задайте значение для свойства EmptyPointValue. Чтобы вставить пустые точки со средним значением предыдущей и последующей точек данных, выберите **Среднее**. Чтобы вставить пустые точки с нулевым значением, выберите **Ноль**.  
  
## <a name="see-also"></a>См. также  
 [Добавление фильтров набора данных, фильтров области данных и фильтры групп &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Типы диаграмм &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [Добавление разрывов шкалы диаграммы &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-scale-breaks-to-a-chart-report-builder-and-ssrs.md)   
 [Диаграммы &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
