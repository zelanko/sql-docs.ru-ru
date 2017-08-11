---
title: "Добавление спарклайнов и гистограмм (построитель отчетов и службы SSRS) | Документы Microsoft"
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
ms.assetid: 0b297c2e-d48b-41b0-aabd-29680cdcdb05
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a9f084fc55a0f3011a40c6f2d8a2cfcdf61dc9f2
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="add-sparklines-and-data-bars-report-builder-and-ssrs"></a>Добавление спарклайнов и гистограмм (построитель отчетов и службы SSRS)
  Sparkline-графики и гистограммы — это маленькие, не требовательные к ресурсам диаграммы, которые передают большой объем данных без ненужных подробностей. Дополнительные сведения см. в разделе [Спарклайны и гистограммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
 В отчетах [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с разбиением на страницы спарклайны и гистограммы обычно размещаются в ячейках в таблице или матрице. Sparkline-графики обычно показывают только одну последовательность. Гистограммы могут содержать одну или несколько точек данных. Как sparkline-графики, так и гистограммы представляют результат повтора рядов для всех строк в таблице или матрице.  
  
## <a name="to-add-a-sparkline-or-data-bar-to-a-table-or-matrix"></a>Добавление в таблицу или матрицу спарклайн-графика или гистограммы  
  
1.  Если это еще не сделано, создайте [таблицу](../../reporting-services/report-design/tables-report-builder-and-ssrs.md) или [матрицу](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md) с данными, которые необходимо отобразить.  
  
2.  Вставьте столбец в таблицу или матрицу. Дополнительные сведения см. в разделе [Вставка или удаление столбца (построитель отчетов и службы SSRS)](../../reporting-services/report-design/insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  На вкладке **Вставка** выберите **Спарклайн-график** или **Гистограмма**, а затем щелкните ячейку в новом столбце.  
  
    > [!NOTE]  
    >  Возможность добавления sparkline-графика в группу сведений таблицы не предусмотрена. Sparkline-график должен находиться в ячейке, связанной с группой.  
  
4.  В диалоговом окне **Изменение типа спарклайна или гистограммы** выберите необходимый тип спарклайна и гистограммы, а затем нажмите кнопку **ОК**.  
  
5.  Щелкните спарклайн-график или гистограмму.  
  
     Откроется панель **Данные гистограммы** .  
  
6.  В области **Значения** щелкните **Добавить поля** символ "плюс" (**+**), а затем щелкните поле, для значений которого необходимо создать диаграмму.  
  
7.  В области **Группы категорий** щелкните **Добавить поля** символ "плюс" (**+**), а затем щелкните поле, значения которого необходимо сгруппировать.  
  
     Обычно для sparkline-графиков и гистограмм к области **Группа рядов** не добавляются поля, поскольку для каждой строки необходим один ряд.  
  
## <a name="see-also"></a>См. также  
 [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Выравнивание данных в диаграмме в таблице или матрице (построитель отчетов и службы SSRS)](../../reporting-services/report-design/align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  
