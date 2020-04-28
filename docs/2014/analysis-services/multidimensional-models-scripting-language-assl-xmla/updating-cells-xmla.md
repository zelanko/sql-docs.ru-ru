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
ms.openlocfilehash: f0eab50aa7e70aedee93eef2cefee648e6ceb5c9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81387894"
---
# <a name="updating-cells-xmla"></a>Обновление ячеек (XML для аналитики)
  Команду [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) можно использовать для изменения значения одной или нескольких ячеек куба, включенных для обратной записи куба. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранит обновленные сведения в отдельной таблице обратной записи для каждой секции, содержащей обновляемые [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ячейки.  
  
> [!NOTE]  
>  Команда `UpdateCells` не поддерживает операции выделения памяти во время обратной записи куба. Чтобы использовать выделенную обратную запись, необходимо использовать команду [инструкции](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) для отправки инструкции UPDATE многомерных выражений (MDX). Дополнительные сведения см. в разделе [инструкция UPDATE CUBE &#40;&#41;многомерных выражений ](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Указание ячеек  
 Свойство [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) `UpdateCells` команды содержит обновляемые ячейки. Каждая ячейка в свойстве `Cell` указывается при помощи ее порядкового номера. Концептуально, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ячейки в Кубе нумеруются так, как если бы куб был *p*многомерным массивом, где *p* — это число осей. Адресация ячеек осуществляется по строкам. На следующем рисунке показана формула для вычисления порядкового номера ячейки.  
  
 ![Формула вычисления порядкового номера ячейки](../../analysis-services/dev-guide/media/cellordinalformula.gif "Формула вычисления порядкового номера ячейки")  
  
 Когда вы узнаете порядковый номер ячейки, можно указать предполагаемое значение ячейки в свойстве [значение](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) свойства [ячейки](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) .  
  
## <a name="see-also"></a>См. также:  
 [Элемент Update &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Разработка с использованием XMLA в службах Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
