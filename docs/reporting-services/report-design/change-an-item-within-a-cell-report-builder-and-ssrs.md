---
title: "Изменение элемента в ячейке (построитель отчетов и службы SSRS) | Документы Майкрософт"
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
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
caps.latest.revision: "8"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: cf872e237310d4dfc9c68fd5a6bd25118a626aec
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="change-an-item-within-a-cell-report-builder-and-ssrs"></a>Изменение элемента в ячейке (построитель отчетов и службы SSRS)
В отчетах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с разбиением на страницы заменять новыми элементами отчета можно только элементы, не являющиеся контейнерами, например текстовые поля, линии и рисунки. Например, можно перетащить таблицу в текстовое поле, чтобы заменить его этой таблицей.  
  
 Если ячейка содержит прямоугольник, список, таблицу или матрицу, то новый элемент добавляется в контейнер, а не заменяет его. Чтобы заменить элемент-контейнер новым элементом, вначале его необходимо удалить. В результате контейнер будет заменен текстовым полем, которое затем можно будет заменить другим элементом.  
  
 По умолчанию все ячейки области данных таблицы, матрицы и списка содержат текстовые поля.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-an-item-within-a-cell"></a>Изменение элемента в ячейке  
  
-   На вкладке **Вставка** в группе **Области данных** или **Элементы отчета** щелкните элемент, который требуется добавить в отчет, а затем щелкните отчет. Элемент будет добавлен в отчет.  
  
> [!NOTE]  
>  После перетаскивания в ячейку элемента отчета, представляющего собой изображение, открывается диалоговое окно **Свойства изображения** , позволяющее задавать такие свойства, как источник изображения, прежде чем изображение будет добавлено к ячейке.  
  
## <a name="see-also"></a>См. также  
 [Изображения, текстовые поля, прямоугольники и линии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/images-text-boxes-rectangles-and-lines-report-builder-and-ssrs.md)   
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
