---
title: Обновление ячеек (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 56c4313ea77fc342c2d7ac4fb142d922038948ca
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60155554"
---
# <a name="updating-cells-xmla"></a>Обновление ячеек (XML для аналитики)
  Можно использовать [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) команду, чтобы изменить значение одной или нескольких ячеек в кубе включена для обратной записи куба. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] хранит обновленную информацию в отдельной таблице обратной записи для каждой секции, содержащей обновляемые ячейки.  
  
> [!NOTE]  
>  Команда `UpdateCells` не поддерживает операции выделения памяти во время обратной записи куба. Чтобы использовать выделенный обратной записи, следует использовать [инструкции](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) команду, чтобы отправить инструкцию UPDATE многомерных выражений (MDX). Дополнительные сведения см. в разделе [инструкция UPDATE CUBE &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Указание ячеек  
 [Ячейки](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) свойство `UpdateCells` команда содержит ячейки, которые необходимо обновить. Каждая ячейка в свойстве `Cell` указывается при помощи ее порядкового номера. По существу [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] нумеруют ячейки в кубе, как если бы куб представлял *p*-мерный массив, где *p* — это число осей. Адресация ячеек осуществляется по строкам. На следующем рисунке показана формула для вычисления порядкового номера ячейки.  
  
 ![Формула для вычисления порядкового номера ячейки](../../../2014/analysis-services/dev-guide/media/cellordinalformula.gif "формулу для вычисления порядкового номера ячейки")  
  
 Определив порядковый номер ячейки, можно указать требуемое значение ячейки в [значение](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) свойство [ячейки](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) свойство.  
  
## <a name="see-also"></a>См. также  
 [Элемент Update &#40;XML для Аналитики&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Разработка с использованием XMLA в службах Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
