---
title: Обновление ячеек (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d1b25b30623ddcdfe4c21442d15fd0cfa0966cc6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275980"
---
# <a name="updating-cells-xmla"></a>Обновление ячеек (XML для аналитики)
  Можно использовать [UpdateCells](../xmla/xml-elements-commands/updatecells-element-xmla.md) команду, чтобы изменить значение одной или нескольких ячеек в кубе включена для обратной записи куба. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] хранит обновленную информацию в отдельной таблице обратной записи для каждой секции, содержащей обновляемые ячейки.  
  
> [!NOTE]  
>  Команда `UpdateCells` не поддерживает операции выделения памяти во время обратной записи куба. Чтобы использовать выделенный обратной записи, следует использовать [инструкции](../xmla/xml-elements-commands/statement-element-xmla.md) команду, чтобы отправить инструкцию UPDATE многомерных выражений (MDX). Дополнительные сведения см. в разделе [инструкция UPDATE CUBE &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Указание ячеек  
 [Ячейки](../xmla/xml-elements-properties/cell-element-xmla.md) свойство `UpdateCells` команда содержит ячейки, которые необходимо обновить. Каждая ячейка в свойстве `Cell` указывается при помощи ее порядкового номера. По существу [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] нумеруют ячейки в кубе, как если бы куб представлял *p*-мерный массив, где *p* — это число осей. Адресация ячеек осуществляется по строкам. На следующем рисунке показана формула для вычисления порядкового номера ячейки.  
  
 ![Формула для вычисления порядкового номера ячейки](../../../2014/analysis-services/dev-guide/media/cellordinalformula.gif "формулу для вычисления порядкового номера ячейки")  
  
 Определив порядковый номер ячейки, можно указать требуемое значение ячейки в [значение](../xmla/xml-elements-properties/value-element-xmla.md) свойство [ячейки](../xmla/xml-elements-properties/cell-element-xmla.md) свойство.  
  
## <a name="see-also"></a>См. также  
 [Элемент Update &#40;XML для Аналитики&#41;](../xmla/xml-elements-commands/update-element-xmla.md)   
 [Разработка с использованием XMLA в службах Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
