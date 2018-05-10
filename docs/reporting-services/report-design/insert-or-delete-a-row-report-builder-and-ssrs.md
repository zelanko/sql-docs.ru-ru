---
title: Вставка или удаление строки (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b9642af3-b3ae-4f78-b0be-8f96b79fc313
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bddaad898b87e97aafbcd6fa7f856e373373a3b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="insert-or-delete-a-row-report-builder-and-ssrs"></a>Вставка или удаление строки (построитель отчетов и службы SSRS)
Можно добавить или удалить строки в области данных табликса в отчете с разбиением на страницы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Областью данных табликса может быть таблица, матрица или список. Следующие процедуры не применяются к области данных диаграммы и датчика.  
  
 В области данных табликса можно добавлять строки, связанные с группой (внутри группы) или не связанные с группой (вне группы). Строка, находящаяся внутри группы, повторяется один раз для уникального значения группы. Например, строка в группе, основанной на значении столбца данных и содержащей имена цветов, повторяется один раз для каждого отдельного имени цвета. Что касается вложенных групп, то строка может находиться вне дочерней группы, но должна находиться в родительской группе. В этом случае строка повторяется один раз для каждого уникального значения в родительской группе.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-select-a-data-region-so-the-row-and-column-handles-appear"></a>Выделение области данных с целью отображения маркеров строки и столбца  
  
-   В конструкторе щелкните левый верхний угол области данных табликса, чтобы поверх и рядом с ней появились маркеры столбца и строки.  
  
     Дополнительные сведения об областях данных см. в разделе [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md).  
  
## <a name="to-insert-a-row-in-a-selected-data-region"></a>Вставка строки в выделенную область данных  
  
-   Щелкните правой кнопкой мыши маркер строки, куда нужно вставить строку, выберите команду **Вставить строку**, а затем выберите **Выше** или **Ниже**.  
  
     \- или -  
  
-   Щелкните правой кнопкой мыши ячейку области данных, куда нужно вставить строку, выберите команду **Вставить строку**, а затем выберите **Выше** или **Ниже**.  
  
## <a name="to-delete-a-row-from-a-selected-data-region"></a>Удаление строки из выделенной области данных  
  
-   Выберите строку или строки, которые нужно удалить, щелкните правой кнопкой мыши маркер одной из выбранных строк и выберите команду **Удалить строки**.  
  
     \- или -  
  
-   Щелкните правой кнопкой мыши ячейку области данных, где нужно удалить строку, и выберите команду **Удалить строки**.  
  
## <a name="to-insert-a-row-in-a-group-in-a-selected-data-region"></a>Вставка строки в группу в выделенной области данных  
  
-   Щелкните правой кнопкой мыши ячейку группы строк в области группы строк в области данных табликса там, где нужно вставить строку, выберите команду **Вставить строку**и выберите **Выше — снаружи группы**, **Выше — внутри группы**, **Ниже — внутри группы**или **Ниже — снаружи группы**.  
  
     Строка добавится внутри или снаружи группы, представленной выбранной ячейкой группы строк.  
  
## <a name="to-delete-a-row-from-a-group-in-a-selected-data-region"></a>Удаление строки из группы в выделенной области данных  
  
-   Щелкните правой кнопкой мыши ячейку группы строк в области данных табликса там, где нужно удалить строку, и выберите команду **Удалить строки**.  
  
## <a name="see-also"></a>См. также:  
 [Область данных табликса (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Основные сведения о группах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/understanding-groups-report-builder-and-ssrs.md)   
 [Таблицы &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Матрицы &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Списки &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)     
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
