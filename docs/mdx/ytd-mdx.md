---
title: "YTD (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: YTD
dev_langs: kbMDX
helpviewer_keywords: Ytd function
ms.assetid: b77fdba2-d4a9-4271-8c21-c1f12eba526d
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 89221e4525cdaaaedd3b891b071b6810bac71fc1
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="ytd-mdx"></a>Ytd (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает набор из одноуровневых элементов того же уровня, что и данный элемент, начиная с первого такого элемента и заканчивая данным элементом, в соответствии с ограничениями *год* уровня в измерении времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Ytd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Замечания  
 Если выражение элемента не указано, по умолчанию используется текущий элемент первой иерархии с уровнем типа *лет* в первом измерении типа *время* в группе мер.  
  
 **Ytd** функция — это функция ярлык для [PeriodsToDate](../mdx/periodstodate-mdx.md) функция которых равно свойство Type атрибута иерархии, на котором основан уровень *лет*. Таким образом, вызов `Ytd(Member_Expression)` эквивалентен вызову `PeriodsToDate(Year_Level_Expression,Member_Expression)`. Обратите внимание, что эта функция не будет работать, если свойство Type имеет значение *FiscalYears*.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается сумма `Measures.[Order Quantity]` член, суммарный за первые восемь месяцев календарного 2003, содержащихся в `Date` измерения, от **Adventure Works** куба.  
  
```  
WITH MEMBER [Date].[Calendar].[First8MonthsCY2003] AS  
    Aggregate(  
        YTD([Date].[Calendar].[Month].[August 2003])  
    )  
SELECT   
    [Date].[Calendar].[First8MonthsCY2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 **С начала года** часто используется в сочетании с без указания параметров, это значит, что [CurrentMember &#40; Многомерные Выражения &#41; ](../mdx/currentmember-mdx.md) функция отображения совокупный итог с начала года в отчете, как показано в следующем запросе:  
  
 `WITH MEMBER MEASURES.YTDDEMO AS`  
  
 `AGGREGATE(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDDEMO} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
