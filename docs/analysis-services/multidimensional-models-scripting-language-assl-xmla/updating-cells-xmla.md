---
title: Обновление ячеек (XMLA) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1e886925621378aa5d01cc77a74edf0e1ea246cc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="updating-cells-xmla"></a>Обновление ячеек (XML для аналитики)
  Можно использовать [UpdateCells](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md) команду, чтобы изменить значение одного или нескольких ячеек в кубе включена для обратной записи куба. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Сохраняет обновленные данные в отдельной таблице обратной записи для каждой секции, содержащей обновляемые ячейки.  
  
> [!NOTE]  
>  **UpdateCells** команда не поддерживает операции выделения памяти во время обратной записи куба. Чтобы использовать выделенный обратной записи, следует использовать [инструкции](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) команду, чтобы отправить инструкции UPDATE многомерных выражений (MDX). Дополнительные сведения см. в разделе [инструкция UPDATE CUBE &#40;многомерных Выражений&#41;](../../mdx/mdx-data-manipulation-update-cube.md).  
  
## <a name="specifying-cells"></a>Указание ячеек  
 [Ячейки](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) свойство **UpdateCells** команда содержит подлежащие обновлению ячейки. Необходимо указать в каждой ячейке **ячейки** свойства, используя порядковый номер этой ячейки. По существу [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] числа ячеек в кубе, как если бы куб представлял *p*-мерный массив, где *p* — число осей. Адресация ячеек осуществляется по строкам. На следующем рисунке показана формула для вычисления порядкового номера ячейки.  
  
 ![Формула для вычисления порядкового номера ячейки](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/media/cellordinalformula.gif "формула для вычисления порядкового номера ячейки")  
  
 Зная порядковый номер ячейки, можно указать требуемое значение ячейки в [значение](../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md) свойство [ячейки](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) свойство.  
  
## <a name="see-also"></a>См. также  
 [Обновить элемент & #40; XML для Аналитики & #41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
