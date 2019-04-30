---
title: YTD (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 67df625611f2451c3442d5d59b56c76dfc14a74a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63295163"
---
# <a name="ytd-mdx"></a>Ytd (многомерные выражения)


  Возвращает набор из того же уровня элементов на одном уровне, что и данный элемент, начиная с первого такого элемента и заканчивая данным элементом, в соответствии с ограничениями *год* уровня в измерении времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Ytd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 Если выражение элемента не указано, по умолчанию используется текущий элемент или первый в иерархии с уровнем типа *лет* в первом измерении типа *время* в группе мер.  
  
 **Ytd** функция является сокращенным вариантом функции для [PeriodsToDate](../mdx/periodstodate-mdx.md) функции, где свойство Type атрибута иерархии, на котором основан уровень присваивается *лет*. Таким образом, вызов `Ytd(Member_Expression)` эквивалентен вызову `PeriodsToDate(Year_Level_Expression,Member_Expression)`. Обратите внимание, что эта функция не будет работать, если свойство Type имеет значение *FiscalYears*.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается сумма `Measures.[Order Quantity]` член, вычисленная за первые восемь месяцев календарного 2003, которые содержатся в `Date` измерения, от **Adventure Works** куба.  
  
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
  
 **С начала года** часто используется в сочетании с без указания параметров, что означает, что [CurrentMember &#40;многомерных Выражений&#41; ](../mdx/currentmember-mdx.md) функции отображения совокупный итог с начала года в отчете, как показано на Следующий запрос:  
  
 `WITH MEMBER MEASURES.YTDDEMO AS`  
  
 `AGGREGATE(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDDEMO} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
