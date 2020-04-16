---
title: Обновление ячеек (XMLA) Документы Майкрософт
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
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81387894"
---
# <a name="updating-cells-xmla"></a>Обновление ячеек (XML для аналитики)
  Вы можете использовать команду [UpdateCells,](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) чтобы изменить значение одной или нескольких ячеек в кубе, включенном для обратного отсылки кубиков. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранит обновленную информацию в отдельной таблице списания для каждого раздела, содержащего ячейки для [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] обновления.  
  
> [!NOTE]  
>  Команда `UpdateCells` не поддерживает операции выделения памяти во время обратной записи куба. Для использования выделенного списания следует использовать команду [«Заявление»](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) для отправки многомерного оператора (MDX) UPDATE. Для получения дополнительной информации смотрите [заявление UPDATE CUBE &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
## <a name="specifying-cells"></a>Указание ячеек  
 Свойство [ячейки](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) `UpdateCells` команды содержит ячейки, которые должны быть обновлены. Каждая ячейка в свойстве `Cell` указывается при помощи ее порядкового номера. Концептуально, цифры клетки в кубе, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] как если бы куб был *р-мерный*массив, где *р* число осей. Адресация ячеек осуществляется по строкам. На следующем рисунке показана формула для вычисления порядкового номера ячейки.  
  
 ![Формула вычисления порядкового номера ячейки](../../analysis-services/dev-guide/media/cellordinalformula.gif "Формула вычисления порядкового номера ячейки")  
  
 После того, как вы знаете, ординаторный номер ячейки, вы можете указать предполагаемое значение ячейки в свойстве [Значения](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) свойства [ячейки.](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)  
  
## <a name="see-also"></a>См. также:  
 [Элемент обновления &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Разработка с использованием XMLA в службах Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
