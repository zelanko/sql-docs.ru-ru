---
title: "Обновление ячеек (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 10803f4f2e3356d996a7c524c69ccd5121569a3e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="updating-cells-xmla"></a>Обновление ячеек (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Можно использовать [UpdateCells](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md) команду, чтобы изменить значение одного или нескольких ячеек в кубе включена для обратной записи куба. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] сохраняют обновленную информацию в отдельной таблице обратной записи для каждой секции, содержащей обновляемые ячейки.  
  
> [!NOTE]  
>  **UpdateCells** команда не поддерживает операции выделения памяти во время обратной записи куба. Чтобы использовать выделенный обратной записи, следует использовать [инструкции](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) команду, чтобы отправить инструкции UPDATE многомерных выражений (MDX). Дополнительные сведения см. в разделе [инструкция UPDATE CUBE &#40; Многомерные Выражения &#41; ](../../mdx/mdx-data-manipulation-update-cube.md).  
  
## <a name="specifying-cells"></a>Указание ячеек  
 [Ячейки](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) свойство **UpdateCells** команда содержит подлежащие обновлению ячейки. Необходимо указать в каждой ячейке **ячейки** свойства, используя порядковый номер этой ячейки. По существу [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] числа ячеек в кубе, как если бы куб представлял *p*-мерный массив, где *p* — число осей. Адресация ячеек осуществляется по строкам. На следующем рисунке показана формула для вычисления порядкового номера ячейки.  
  
 ![Формула для вычисления порядкового номера ячейки](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/media/cellordinalformula.gif "формула для вычисления порядкового номера ячейки")  
  
 Зная порядковый номер ячейки, можно указать требуемое значение ячейки в [значение](../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md) свойство [ячейки](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) свойство.  
  
## <a name="see-also"></a>См. также:  
 [Обновить элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Разработка с использованием XMLA в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
