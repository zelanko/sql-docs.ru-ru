---
title: Типы диаграмм (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10423"
ms.assetid: 57b00017-69ae-4e71-8d78-44744e208ac7
caps.latest.revision: 10
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: f69c4a6dd5f2593650067be51eae3b63e49dcd96
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36094724"
---
# <a name="chart-types-report-builder-and-ssrs"></a>Типы диаграмм (построитель отчетов и службы SSRS)
  Важно выбрать тип диаграммы, подходящий для типа представляемых данных. От этого зависит, насколько успешно можно будет интерпретировать данные после их вывода на диаграмме. Например, если набор данных содержит количество точек данных, сравнимое с размером диаграммы, то может оказаться более успешным представление данных с использованием диаграммы с областями, графика или точечной диаграммы. Сведения о том, как подготовить данные в зависимости от выбранного типа диаграммы. в разделе [диаграммы &#40;построитель отчетов и службы SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="choosing-a-chart-type"></a>Выбор типа диаграммы  
 Диаграмма каждого типа обладает уникальными характеристиками, позволяющими наилучшим образом представить визуально конкретный набор данных. Для отображения данных можно использовать диаграммы любого типа, но удобство чтения данных повышается, если применяется тип диаграммы, подходящий для конкретных данных, учитывая то, что должно быть показано в отчете. В следующей таблице собраны характеристики диаграммы, от которых зависит применимость диаграммы для конкретного набора данных.  
  
 Тип диаграммы можно изменить после ее создания. Дополнительные сведения см. в статье [Изменение типа диаграммы (построитель отчетов и службы SSRS)](change-a-chart-type-report-builder-and-ssrs.md).  
  
 Примеры многих из этих типов диаграмм доступны в качестве образцов отчетов. Дополнительные сведения о скачивании образцов отчетов см. в статье [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][(Примеры отчетов построителя отчетов и конструктора отчетов)](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
|Тип диаграммы|Отображение данных отношений|Отображение данных об акциях|Отображение линейных данных|Отображение многозначных данных|  
|----------------|------------------------|------------------------|-------------------------|-------------------------------|  
|[Диаграммы с областями &#40;отчетов построителя отчетов и службы SSRS&#41;](area-charts-report-builder-and-ssrs.md)|||![Доступно](../media/greencheck.gif "Доступно")||  
|[Линейчатые диаграммы &#40;отчетов построителя отчетов и службы SSRS&#41;](bar-charts-report-builder-and-ssrs.md)|||![Доступно](../media/greencheck.gif "Доступно")||  
|[Гистограммы](sparklines-and-data-bars-report-builder-and-ssrs.md)|||![Доступно](../media/greencheck.gif "Доступно")||  
|[Гистограмма с накоплением &#40;отчетов построителя отчетов и службы SSRS&#41;](column-charts-report-builder-and-ssrs.md)|||![Доступно](../media/greencheck.gif "Доступно")||  
|[Линейчатые диаграммы &#40;отчетов построителя отчетов и службы SSRS&#41;](line-charts-report-builder-and-ssrs.md)|||![Доступно](../media/greencheck.gif "Доступно")||  
|[Круговые диаграммы &#40;отчетов построителя отчетов и службы SSRS&#41;](pie-charts-report-builder-and-ssrs.md)|![Доступно](../media/greencheck.gif "Доступно")||||  
|[Полярная диаграмма &#40;отчетов построителя отчетов и службы SSRS&#41;](polar-charts-report-builder-and-ssrs.md)|![Доступно](../media/greencheck.gif "Доступно")||||  
|[Диаграммы диапазонов &#40;отчетов построителя отчетов и службы SSRS&#41;](range-charts-report-builder-and-ssrs.md)|||![Доступно](../media/greencheck.gif "Доступно")|![Доступно](../media/greencheck.gif "Доступно")|  
|[Точечные диаграммы &#40;отчетов построителя отчетов и службы SSRS&#41;](scatter-charts-report-builder-and-ssrs.md)|![Доступно](../media/greencheck.gif "Доступно")||![Доступно](../media/greencheck.gif "Доступно")||  
|[Фигурные диаграммы &#40;отчетов построителя отчетов и службы SSRS&#41;](shape-charts-report-builder-and-ssrs.md)|![Доступно](../media/greencheck.gif "Доступно")||||  
|[Спарклайны](sparklines-and-data-bars-report-builder-and-ssrs.md)|![Доступно](../media/greencheck.gif "Доступно")|![Доступно](../media/greencheck.gif "Доступно")|![Доступно](../media/greencheck.gif "Доступно")|![Доступно](../media/greencheck.gif "Доступно")|  
|[Stock диаграммы &#40;отчетов построителя отчетов и службы SSRS&#41;](stock-charts-report-builder-and-ssrs.md)||![Доступно](../media/greencheck.gif "Доступно")||![Доступно](../media/greencheck.gif "Доступно")|  
  
## <a name="see-also"></a>См. также  
 [Диаграммы (построитель отчетов и службы SSRS)](charts-report-builder-and-ssrs.md)   
 [Точки данных со значением NULL и пустые точки в диаграммах (построитель отчетов и службы SSRS)](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [Добавление диаграммы в отчет &#40;отчетов построителя отчетов и службы SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)  
  
  