---
title: Графики (построитель отчетов) | Документация Майкрософт
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 194e6679-890d-4a3e-a756-130d32ef7e29
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b0e1308f7dfac834e6c50062a199403023088a59
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "77081969"
---
# <a name="line-charts-report-builder-and-ssrs"></a>Графики (построитель отчетов и службы SSRS)
  График отображает ряды значений в виде точек, соединенных линией. Графики используются для представления больших объемов данных, распределенных на непрерывном отрезке времени. Дополнительные сведения о добавлении данных на график см. в разделе [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md).  
  
 На следующем рисунке показан график, содержащий три ряда.  
  
 ![График](../../reporting-services/report-design/media/rs-linechart.gif "График")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>Варианты  
  
-   **Гладкий график**. График, в котором вместо обычных линий используются изогнутые.  
  
-   **Ступенчатый график**. График, в котором вместо обычных линий используются ступенчатые. В ступенчатом графике точки соединяются линией, напоминающей ступеньки на лестнице.  
  
-   **Спарклайн-графики**. Вариации линейного графика, которые показывают только последовательность линий в ячейке таблицы или матрицы. Дополнительные сведения см. в разделе [Спарклайны и гистограммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="data-considerations-for-line-charts"></a>Соображения о данных в графиках  
  
-   Усилить зрительный эффект графика можно, увеличив ширину границы до 3 и добавив смещение тени со значением 1. В результате график станет намного более выразительным. Если понадобится сменить тип диаграммы с графика на другой тип, то может понадобиться присвоить этим свойствам значения по умолчанию.  
  
-   Ели в наборе данных существуют пустые значения, график заполнит их линиями-заполнителями для обеспечения непрерывности графика. Если отображение этих линий нежелательно, набор данных можно представить с помощью дискретных типов диаграмм, например линейчатых диаграмм или гистограмм.  
  
-   Для создания линии графику требуются как минимум 2 точки.  Если в наборе данных существует только одна точка данных, то график будет отображен как единственный маркер точки данных.  
  
-   Ряд, отображенный в виде линии, не займет много места в области диаграммы.  В связи с этим графики часто совмещаются с другими типами диаграмм, например гистограммами. Однако график не может быть совмещен с линейчатыми, полярными, круговыми и фигурными диаграммами.  
  
## <a name="see-also"></a>См. также:  
 [Линейчатые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)   
 [Гистограммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/column-charts-report-builder-and-ssrs.md)   
 [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Типы диаграмм (построитель отчетов и службы SSRS)](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [Диаграммы с областями (построитель отчетов и службы SSRS)](../../reporting-services/report-design/area-charts-report-builder-and-ssrs.md)   
 [Точки данных со значением NULL и пустые точки в диаграммах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
