---
title: Изменение элемента в ячейке (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.suite: pro-bi
ms.topic: conceptual
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3e1510754208022fd700ec81f1dda845c998c016
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43275144"
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
  
## <a name="see-also"></a>См. также:  
 [Изображения, текстовые поля, прямоугольники и линии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/images-text-boxes-rectangles-and-lines-report-builder-and-ssrs.md)   
 [Таблицы, матрицы и списки (построитель отчетов и службы SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
