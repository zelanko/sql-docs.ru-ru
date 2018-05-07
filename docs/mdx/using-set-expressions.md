---
title: Выражения наборов | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- expressions [MDX], set
- tuples
- set expressions [MDX]
ms.assetid: 88d65872-0cbe-4c95-b36f-e1aa4ac8ed07
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 8e300f47b7f01ade259b4b8bc1a63a0b105e336f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-set-expressions"></a>Выражения наборов
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Набор — это упорядоченный список, состоящий из кортежей (может не содержать ни одного кортежа). Набор, который не содержит кортежей, называется пустым.  
  
 Полное выражение набора состоит из нуля или нескольких явно заданных кортежей, заключенных в фигурные скобки.  
  
 {[{ *Tuple_expression* | *Member_expression* } [, { *Tuple_expression* | *Member_expression* }]...]}  
  
 Выражения элементов, указанные в выражении набора, преобразуются в выражения одноэлементных кортежей.  
  
## <a name="example"></a>Пример  
 В следующем примере показаны два выражения набора, используемые по осям столбцов и строк запроса:  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]} ON COLUMNS,`  
  
 `{([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),`  
  
 `([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),`  
  
 `([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 По оси столбцов набор  
  
 {[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}  
  
 состоит из двух элементов из измерения Measures. По оси строк набор  
  
 {([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),  
  
 ([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),  
  
 ([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}  
  
 состоит из трех кортежей, каждый из которых содержит две явные ссылки на элементы в иерархии «Категории продуктов» измерения «Продукт» и иерархии «Календарь» измерения «Дата».  
  
 Примеры функций, возвращающих наборы см. в разделе [работа с элементами, кортежами и наборами &#40;многомерных Выражений&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>См. также  
 [Выражения &#40;многомерных Выражений&#41;](../mdx/expressions-mdx.md)  
  
  
