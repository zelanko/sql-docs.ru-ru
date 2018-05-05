---
title: Функции наборов | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- set functions [MDX]
ms.assetid: b08ddc9d-38f8-41aa-b791-b5352f1a8783
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b0946bd46910077d2ffe1a2bbd2ffa31be919e75
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-set-functions"></a>Функции наборов
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Функции наборов извлекают наборы из измерений, иерархий и уровней, либо путем обхода абсолютных и относительных мест расположения элементов в этих объектах, формируя набор различными способами.  
  
 Функции наборов, как и функции элементов или кортежей, имеют большое значение для согласования многомерных структур в службах Analysis Services. Они также важны для получения результатов многомерных выражений, поскольку выражения наборов определяют оси многомерных выражений.  
  
 Одна из самых распространенных функций наборов — [элементы &#40;задать&#41; &#40;многомерных Выражений&#41; ](../mdx/members-set-mdx.md) функции, которая возвращает набор, содержащий все элементы из измерения, иерархии или уровня. Ниже приведен пример ее использования в запросе:  
  
 `SELECT`  
  
 `//Returns all of the members on the Measures dimension`  
  
 `[Measures].MEMBERS`  
  
 `ON Columns,`  
  
 `//Returns all of the members on the Calendar Year level of the Calendar Year Hierarchy`  
  
 `//on the Date dimension`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Другая часто используемая функция [Crossjoin &#40;многомерных Выражений&#41; ](../mdx/crossjoin-mdx.md) функции. Она возвращает набор кортежей, представляющий декартово произведение наборов, переданных в нее в качестве параметров. На практике эта функция позволяет создавать «вложенные» или «перекрестные» оси в запросах:  
  
 `SELECT`  
  
 `//Returns all of the members on the Measures dimension`  
  
 `[Measures].MEMBERS`  
  
 `ON Columns,`  
  
 `//Returns a set containing every combination of all of the members`  
  
 `//on the Calendar Year level of the Calendar Year Hierarchy`  
  
 `//on the Date dimension and all of the members on the Category level`  
  
 `//of the Category hierarchy on the Product dimension`  
  
 `Crossjoin(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS,`  
  
 `[Product].[Category].[Category].MEMBERS)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 [Потомков &#40;многомерных Выражений&#41; ](../mdx/descendants-mdx.md) функция работает как **дочерних** работать, но обладает более широкими возможностями. Она возвращает потомки любого элемента на одном и нескольких уровнях иерархии:  
  
 SELECT  
  
 [Measures].[Internet Sales Amount]  
  
 ON Columns,  
  
 //Возвращает набор, содержащий все даты под календарным годом  
  
 //2004 в иерархии «Календарь» измерения «Дата»  
  
 DESCENDANTS(  
  
 [Date]. [Календарь]. [Calendar Year]. & [2004]  
  
 , [Date].[Calendar].[Date])  
  
 ON Rows  
  
 FROM [Adventure Works]  
  
 [Порядок &#40;многомерных Выражений&#41; ](../mdx/order-mdx.md) функция позволяет упорядочить содержимое набора по возрастанию или убыванию в соответствии с конкретным числовым выражением. Следующий запрос возвращает те же элементы по строкам, что и предшествующий, но упорядочивает их по мере Internet Sales Amount:  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//ordered by Internet Sales Amount`  
  
 `ORDER(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `, [Measures].[Internet Sales Amount], BDESC)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Этот запрос также показывает, как набор, возвращенный одной функцией набора (Descendants), может быть передан в качестве параметра в другую функцию набора (Order).  
  
 Фильтрация набора по определенным критериям очень полезна при написании запросов, и для этой цели можно использовать [фильтра &#40;многомерных Выражений&#41; ](../mdx/filter-mdx.md) функции, как показано в следующем примере:  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//where Internet Sales Amount is greater than $70000`  
  
 `FILTER(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `, [Measures].[Internet Sales Amount]>70000)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Существуют и более сложные функции, которые позволяют фильтровать набор другими способами. Например, следующий запрос показывает [TopCount &#40;многомерных Выражений&#41; ](../mdx/topcount-mdx.md) функция возвращает верхние n элементов в наборе:  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing the top 10 Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension by Internet Sales Amount`  
  
 `TOPCOUNT(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `,10, [Measures].[Internet Sales Amount])`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Наконец можно выполнить количество логических операций с помощью функций, таких как [Intersect &#40;многомерных Выражений&#41;](../mdx/intersect-mdx.md), [объединения &#40;многомерных Выражений&#41; ](../mdx/union-mdx.md) и [за исключением &#40;Многомерных Выражений&#41; ](../mdx/except-mdx-function.md) функции. Следующий запрос показывает использование двух последних функций:  
  
 `SELECT`  
  
 `//Returns a set containing the Measures Internet Sales Amount, Internet Tax Amount and`  
  
 `//Internet Total Product Cost`  
  
 `UNION(`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}`  
  
 `, {[Measures].[Internet Total Product Cost]}`  
  
 `)`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//except the January 1st 2004`  
  
 `EXCEPT(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `,{[Date].[Calendar].[Date].&[915]})`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;синтаксис многомерных Выражений&#41;](../mdx/functions-mdx-syntax.md)   
 [С помощью функции-члены](../mdx/using-member-functions.md)   
 [Использование функций кортежей](../mdx/using-tuple-functions.md)  
  
  
