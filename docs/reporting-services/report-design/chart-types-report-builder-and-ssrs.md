---
title: "Диаграммы (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- "10423"
ms.assetid: 57b00017-69ae-4e71-8d78-44744e208ac7
caps.latest.revision: 11
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 7b23da886ccf8fc76cbe8e86a722e4e9a8f3e656
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---

# <a name="chart-types-report-builder-and-ssrs"></a>Типы диаграмм (построитель отчетов и службы SSRS)

Важно выбрать тип диаграммы, подходящий для типа представляемых данных. От этого зависит, насколько успешно можно будет интерпретировать данные после их вывода на диаграмме. Например, если набор данных содержит количество точек данных, сравнимое с размером диаграммы, то может оказаться более успешным представление данных с использованием диаграммы с областями, графика или точечной диаграммы. Обсуждение темы, касающейся подготовки данных в зависимости от выбранного типа диаграммы, см. в разделе [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="choosing-a-chart-type"></a>Выбор типа диаграммы  
 Диаграмма каждого типа обладает уникальными характеристиками, позволяющими наилучшим образом представить визуально конкретный набор данных. Для отображения данных можно использовать диаграммы любого типа, но удобство чтения данных повышается, если применяется тип диаграммы, подходящий для конкретных данных, учитывая то, что должно быть показано в отчете. В следующей таблице собраны характеристики диаграммы, от которых зависит применимость диаграммы для конкретного набора данных.  
  
 Тип диаграммы можно изменить после ее создания. Дополнительные сведения см. в статье [Изменение типа диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/change-a-chart-type-report-builder-and-ssrs.md).  
  
 Примеры многих из этих типов диаграмм доступны в качестве образцов отчетов. Дополнительные сведения о загрузке образцов отчетов см. в разделе [примеры отчетов построителя отчетов и конструктора отчетов](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
|Тип диаграммы|Отображение данных отношений|Отображение данных об акциях|Отображение линейных данных|Отображение многозначных данных|  
|----------------|------------------------|------------------------|-------------------------|-------------------------------|  
|[Диаграммы с областями (построитель отчетов и службы SSRS)](../../reporting-services/report-design/area-charts-report-builder-and-ssrs.md)|||![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")||  
|[Линейчатые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)|||![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")||  
|[Гистограммы](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)|||![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")||  
|[Гистограммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/column-charts-report-builder-and-ssrs.md)|||![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")||  
|[Графики (построитель отчетов и службы SSRS)](../../reporting-services/report-design/line-charts-report-builder-and-ssrs.md)|||![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")||  
|[Круговые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)|![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")||||  
|[Полярные диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/polar-charts-report-builder-and-ssrs.md)|![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")||||  
|[Диаграммы диапазонов (построитель отчетов и службы SSRS)](../../reporting-services/report-design/range-charts-report-builder-and-ssrs.md)|||![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")|![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")|  
|[Точечные диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/scatter-charts-report-builder-and-ssrs.md)|![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")||![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")||  
|[Фигурные диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/shape-charts-report-builder-and-ssrs.md)|![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")||||  
|[Sparkline-графики](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)|![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")|![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")|![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")|![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")|  
|[Биржевые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/stock-charts-report-builder-and-ssrs.md)||![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")||![Доступные](../../reporting-services/report-data/media/greencheck.gif "доступен")|  

## <a name="next-steps"></a>Следующие шаги

[Диаграммы](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
[NULL и пустые точки данных в диаграммах](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
[Добавление диаграммы в отчет](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
