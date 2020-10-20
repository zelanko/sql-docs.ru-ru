---
description: Выражения наборов
title: Использование выражений набора | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ddcdee57bd708bc8eb4c3c07d8e86a70705e01e6
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92193470"
---
# <a name="using-set-expressions"></a>Выражения наборов


  Набор — это упорядоченный список, состоящий из кортежей (может не содержать ни одного кортежа). Набор, который не содержит кортежей, называется пустым.  
  
 Полное выражение набора состоит из нуля или нескольких явно заданных кортежей, заключенных в фигурные скобки.  
  
 {[{ *Tuple_expression*  |  *Member_expression* } [, { *Tuple_expression*  |  *Member_expression* }]...]}  
  
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
  
 {([Продукт]. [Категории продуктов]. [Категория]. & [4], [DATE]. [Календарь]. [Календарный год]. & [2004]),  
  
 ([Продукт]. [Категории продуктов]. [Category]. & [1], [Дата]. [Календарь]. [Календарный год]. & [2003]),  
  
 ([Продукт]. [Категории продуктов]. [Категория]. & [3], [DATE]. [Календарь]. [Календарный год]. & [2004])}  
  
 состоит из трех кортежей, каждый из которых содержит две явные ссылки на элементы в иерархии «Категории продуктов» измерения «Продукт» и иерархии «Календарь» измерения «Дата».  
  
 Примеры функций, которые возвращают наборы, см. [в разделе Работа с элементами, кортежами и наборами &#40;&#41;многомерных выражений ](/analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx).  
  
## <a name="see-also"></a>См. также:  
 [Выражения &#40;&#41;многомерных выражений ](../mdx/expressions-mdx.md)  
  
