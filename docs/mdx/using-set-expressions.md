---
title: "Выражения наборов | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- expressions [MDX], set
- tuples
- set expressions [MDX]
ms.assetid: 88d65872-0cbe-4c95-b36f-e1aa4ac8ed07
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 441931651dbe54b9205a5e02da808f35a2b34844
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="using-set-expressions"></a>Выражения наборов
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
 Примеры функций, возвращающих наборы см. в разделе [работа с членами, кортежей и наборов &#40; Многомерные Выражения &#41; ](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>См. также:  
 [Выражения &#40; Многомерные Выражения &#41;](../mdx/expressions-mdx.md)  
  
  
