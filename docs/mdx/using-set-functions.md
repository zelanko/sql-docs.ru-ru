---
title: Использование функций Set | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 52e0c140acb944a774f5ab167bb81c662e3e32d7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038052"
---
# <a name="using-set-functions"></a>Функции наборов


  Функции наборов извлекают наборы из измерений, иерархий и уровней, либо путем обхода абсолютных и относительных мест расположения элементов в этих объектах, формируя набор различными способами.  
  
 Функции наборов, как и функции элементов или кортежей, имеют большое значение для согласования многомерных структур в службах Analysis Services. Они также важны для получения результатов многомерных выражений, поскольку выражения наборов определяют оси многомерных выражений.  
  
 Одной из наиболее распространенных функций набора являются [члены &#40;set&#41; &#40;функция&#41;многомерных выражений](../mdx/members-set-mdx.md) , которая извлекает набор, содержащий все элементы из измерения, иерархии или уровня. Ниже приведен пример ее использования в запросе:  
  
 `SELECT`  
  
 `//Returns all of the members on the Measures dimension`  
  
 `[Measures].MEMBERS`  
  
 `ON Columns,`  
  
 `//Returns all of the members on the Calendar Year level of the Calendar Year Hierarchy`  
  
 `//on the Date dimension`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Еще одна часто используемая функция — это [Перекрестное &#40;функции&#41;многомерных выражений](../mdx/crossjoin-mdx.md) . Она возвращает набор кортежей, представляющий декартово произведение наборов, переданных в нее в качестве параметров. На практике эта функция позволяет создавать «вложенные» или «перекрестные» оси в запросах:  
  
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
  
 [Потомки &#40;функции&#41;многомерных выражений](../mdx/descendants-mdx.md) похожи на функции **дочерних** функций, но являются более мощными. Она возвращает потомки любого элемента на одном и нескольких уровнях иерархии:  
  
 SELECT  
  
 [Measures].[Internet Sales Amount]  
  
 ON Columns,  
  
 //Возвращает набор, содержащий все даты под календарным годом  
  
 //2004 в иерархии «Календарь» измерения «Дата»  
  
 DESCENDANTS(  
  
 [Дата]. [Календарь]. [Календарный год]. & [2004]  
  
 , [Date].[Calendar].[Date])  
  
 ON Rows  
  
 FROM [Adventure Works]  
  
 Функция [order &#40;&#41;многомерных выражений](../mdx/order-mdx.md) позволяет упорядочить содержимое набора в порядке возрастания или убывания в соответствии с определенным числовым выражением. Следующий запрос возвращает те же элементы по строкам, что и предшествующий, но упорядочивает их по мере Internet Sales Amount:  
  
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
  
 Фильтрация набора в соответствии с определенными критериями очень полезна при написании запросов. для этой цели можно использовать функцию [Filter &#40;многомерных выражений&#41;](../mdx/filter-mdx.md) , как показано в следующем примере:  
  
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
  
 Существуют и более сложные функции, которые позволяют фильтровать набор другими способами. Например, следующий запрос показывает, что функция [TopCount &#40;многомерные выражения&#41;](../mdx/topcount-mdx.md) возвращает верхние n элементов в наборе:  
  
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
  
 Наконец, можно выполнить несколько операций логического набора с помощью таких функций, как [Intersect &#40;многомерные выражения&#41;](../mdx/intersect-mdx.md), [Union &#40;MDX&#41;](../mdx/union-mdx.md) и [except &#40;функций&#41;многомерных выражений](../mdx/except-mdx-function.md) . Следующий запрос показывает использование двух последних функций:  
  
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
  
## <a name="see-also"></a>См. также:  
 [Функции &#40;синтаксиса многомерных выражений&#41;](../mdx/functions-mdx-syntax.md)   
 [Использование функций элементов](../mdx/using-member-functions.md)   
 [Функции кортежей](../mdx/using-tuple-functions.md)  
  
  
