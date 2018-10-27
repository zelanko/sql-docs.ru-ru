---
title: Обновление ячеек (XMLA) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0cfee2adf9d730b458fd482317d16d963f15ebc1
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50146780"
---
# <a name="updating-cells-xmla"></a>Обновление ячеек (XML для аналитики)
  Можно использовать [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) команду, чтобы изменить значение одной или нескольких ячеек в кубе включена для обратной записи куба. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] хранит обновленную информацию в отдельной таблице обратной записи для каждой секции, содержащей обновляемые ячейки.  
  
> [!NOTE]  
>  **UpdateCells** команда не поддерживает операции выделения памяти во время обратной записи куба. Чтобы использовать выделенный обратной записи, следует использовать [инструкции](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) команду, чтобы отправить инструкцию UPDATE многомерных выражений (MDX). Дополнительные сведения см. в разделе [инструкция UPDATE CUBE &#40;многомерных Выражений&#41;](../../mdx/mdx-data-manipulation-update-cube.md).  
  
## <a name="specifying-cells"></a>Указание ячеек  
 [Ячейки](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) свойство **UpdateCells** команда содержит ячейки, которые необходимо обновить. Каждая ячейка в **ячейки** свойства, используя порядковый номер этой ячейки. По существу [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] нумеруют ячейки в кубе, как если бы куб представлял *p*-мерный массив, где *p* — это число осей. Адресация ячеек осуществляется по строкам. На следующем рисунке показана формула для вычисления порядкового номера ячейки.  
  
 ![Формула для вычисления порядкового номера ячейки](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/media/cellordinalformula.gif "формулу для вычисления порядкового номера ячейки")  
  
 Определив порядковый номер ячейки, можно указать требуемое значение ячейки в [значение](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) свойство [ячейки](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) свойство.  
  
## <a name="see-also"></a>См. также  
 [Элемент Update &#40;XML для Аналитики&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Разработка с использованием XMLA в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
