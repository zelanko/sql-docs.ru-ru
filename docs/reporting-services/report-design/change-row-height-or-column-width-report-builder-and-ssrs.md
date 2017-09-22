---
title: "Изменение высоты строки или ширины столбца (построитель отчетов и службы SSRS) | Документы Microsoft"
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
ms.assetid: f061c204-5cd5-4467-9a9c-8a12803d93ba
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: c13295c229dc4450b9661c25f86d7eacf669787d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/21/2017

---
# <a name="change-row-height-or-column-width-report-builder-and-ssrs"></a>Изменение высоты строки или ширины столбца (построитель отчетов и службы SSRS)
  При установке высоты строк указывается максимальная высота строки в готовом для просмотра отчете. Но по умолчанию текстовые поля в строке расширяются в вертикальном направлении, чтобы вместить все данные во время выполнения отчета, поэтому строка может расширяться по высоте за заданные пределы. Чтобы установить фиксированную высоту строки, необходимо изменить свойства текстового поля так, чтобы они не расширялись автоматически.  
  
 При установке ширины столбца указывается максимальная ширина столбца в готовом для просмотра отчете. Столбцы не расширяются горизонтально, чтобы вместить текст.  
  
 Если ячейка в строке или столбце содержит прямоугольник или область данных, минимальная высота и ширина ячейки определяется высотой содержащегося элемента. Дополнительные сведения см. в разделе [Поведение при подготовке к просмотру (построитель отчетов и службы SSRS)](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-row-height-by-moving-row-handles"></a>Для изменения высоты строки перемещением маркеров строки  
  
1.  В режиме конструктора щелкните в любом месте области данных табликса, чтобы выделить ее. На внешней границе области данных табликса появятся серые маркеры строк.  
  
2.  Поместите указатель мыши на краю нужного маркера строки. Появится двунаправленная стрелка.  
  
3.  Щелкните, чтобы захватить край строки, и перетащите его выше или ниже на нужное расстояние.  
  
### <a name="to-change-row-height-by-setting-cell-properties"></a>Для изменения высоты строки настройкой параметров ячейки  
  
1.  В режиме конструктора щелкните по ячейке в строке таблицы.  
  
     ![Выбранные ячейки в таблице](../../reporting-services/report-design/media/table-selectcell.png "выбранные ячейки в таблице")  
  
2.  На отображаемой вкладке **Свойства** , измените свойство **Высота** , а затем щелкните где-нибудь за пределами вкладки **Свойства** .  
  
     ![Панель свойств для выбранной ячейки таблицы](../../reporting-services/report-design/media/cell-propertiespane.png "панель свойств для выбранной ячейки таблицы")  
  
### <a name="to-prevent-a-row-from-automatically-expanding-vertically"></a>Отключение автоматического расширения строки по вертикали  
  
1.  В режиме конструктора щелкните в любом месте области данных табликса, чтобы выделить ее. На внешней границе области данных табликса появятся серые маркеры строк.  
  
2.  Щелкните маркер, чтобы выбрать строку.  
  
3.  На панели "Свойства" присвойте параметру CanGrow значение **False**.  
  
    > [!NOTE]  
    >  Если панель "Свойства" не появилась, в меню **Вид** выберите пункт **Свойства**.  
  
### <a name="to-change-column-width"></a>Изменение ширины столбца  
  
1.  В режиме конструктора щелкните в любом месте области данных табликса, чтобы выделить ее. На внешней границе области данных табликса появятся серые маркеры столбца.  
  
2.  Поместите указатель мыши на краю нужного маркера столбца. Появится двунаправленная стрелка.  
  
3.  Щелкните, чтобы захватить край столбца, и перетащите его вправо или влево на нужное расстояние.  
  
## <a name="see-also"></a>См. также:  
 [Области данных Табликса (построитель отчетов и службы SSRS)](/sql-docs/docs/reporting-services/report-design/tablix-data-region-report-builder-and-ssrs)   
 [Ячейки области данных Табликса, строк и столбцов (построитель отчетов) и службы SSRS](/sql-docs/docs/reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs)   
 [Таблицы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Матрицы (построитель отчетов и службы SSRS)](/sql-docs/docs/reporting-services/report-design/create-a-matrix-report-builder-and-ssrs)   
 [Списки (построитель отчетов и службы SSRS)](/sql-docs/docs/reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs)   
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
