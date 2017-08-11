---
title: "Линейчатые диаграммы (построитель отчетов и службы SSRS) | Документы Microsoft"
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
ms.assetid: 194e6679-890d-4a3e-a756-130d32ef7e29
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b309753291bfae573be58b124c033d021adb254c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="line-charts-report-builder-and-ssrs"></a>Графики (построитель отчетов и службы SSRS)
  График отображает ряды значений в виде точек, соединенных линией. Графики используются для представления больших объемов данных, распределенных на непрерывном отрезке времени. Дополнительные сведения о добавлении данных на график см. в разделе [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md).  
  
 На следующем рисунке показан график, содержащий три ряда.  
  
 ![График](../../reporting-services/report-design/media/rs-linechart.gif "график")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>Разновидности  
  
-   **Гладкий график**. График, в котором вместо обычных линий используются изогнутые.  
  
-   **Ступенчатый график**. График, в котором вместо обычных линий используются ступенчатые. В ступенчатом графике точки соединяются линией, напоминающей ступеньки на лестнице.  
  
-   **Спарклайн-графики**. Вариации линейного графика, которые показывают только последовательность линий в ячейке таблицы или матрицы. Дополнительные сведения см. в разделе [Спарклайны и гистограммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="data-considerations-for-line-charts"></a>Соображения о данных в графиках  
  
-   Усилить зрительный эффект графика можно, увеличив ширину границы до 3 и добавив смещение тени со значением 1. В результате график станет намного более выразительным. Если понадобится сменить тип диаграммы с графика на другой тип, то может понадобиться присвоить этим свойствам значения по умолчанию.  
  
-   Ели в наборе данных существуют пустые значения, график заполнит их линиями-заполнителями для обеспечения непрерывности графика. Если отображение этих линий нежелательно, набор данных можно представить с помощью дискретных типов диаграмм, например линейчатых диаграмм или гистограмм.  
  
-   Для создания линии графику требуются как минимум 2 точки.  Если в наборе данных существует только одна точка данных, то график будет отображен как единственный маркер точки данных.  
  
-   Ряд, отображенный в виде линии, не займет много места в области диаграммы.  В связи с этим графики часто совмещаются с другими типами диаграмм, например гистограммами. Однако график не может быть совмещен с линейчатыми, полярными, круговыми и фигурными диаграммами.  
  
## <a name="see-also"></a>См. также  
 [Линейчатые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)   
 [Гистограмма с накоплением &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/column-charts-report-builder-and-ssrs.md)   
 [Диаграммы &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Типы диаграмм &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [Диаграммы с областями &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/area-charts-report-builder-and-ssrs.md)   
 [NULL и пустые точки данных в диаграммах &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [Графики и &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
