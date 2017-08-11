---
title: "Объединение ячеек в области данных (построитель отчетов и службы SSRS) | Документы Microsoft"
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
ms.assetid: 43551300-89b2-4f4e-af09-69084324afaf
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c643b94c86109a99e1448093b4b9744924fcd7f7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="merge-cells-in-a-data-region-report-builder-and-ssrs"></a>Объединение ячеек в области данных (построитель отчетов и службы SSRS)
В отчете с разбиением на страницы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно объединить ячейки в области данных, чтобы соединить их, улучшить внешний вид области данных или сформировать метки для групп столбцов и строк.  
  
Объединить можно только ячейки в пределах одной области в области данных: угла, заголовка столбца, определения (или заголовка) группы и текста отчета. Ячейки, относящиеся к разным областям, объединить нельзя. Например, нельзя объединить ячейку из угловой области в области данных с ячейкой из области группы строк. Дополнительные сведения см. разделе [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-merge-cells-in-a-data-region"></a>Объединение ячеек в области данных  
  
1.  В области данных конструктора отчета щелкните первую ячейку для объединения. Удерживая нажатой левую кнопку мыши, перетащите курсор вертикально или горизонтально, чтобы выбрать смежные ячейки. Выбранные ячейки будут выделены.  
  
2.  Щелкните выбранные ячейки правой кнопкой мыши и выберите команду **Объединить ячейки**. Выбранные ячейки будут объединены в одну.  
  
3.  Повторяйте шаги 1 и 2, чтобы объединить другие смежные ячейки в области данных.  
  
## <a name="see-also"></a>См. также  
[Область данных табликса](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)  
 [Tables &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Создание матрицы](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Создание счета-фактуры и формы со списками](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
[Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
