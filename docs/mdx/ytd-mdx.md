---
title: YTD (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2e3fcd823dea5d651cd7be9295fa4c6bba25380c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125764"
---
# <a name="ytd-mdx"></a>Ytd (многомерные выражения)


  Возвращает набор элементов с общим родителем, находящиеся на том же уровне, что и заданный элемент, начиная с первого элемента того же уровня и заканчивая данным элементом, в соответствии с ограничением на уровень *года* в измерении Time.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Ytd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Remarks  
 Если выражение элемента не указано, по умолчанию используется текущий элемент первой иерархии с уровнем *years* в первом измерении типа *time* в группе мер.  
  
 Функция **YTD** является сочетанием клавиш для функции [PeriodsToDate](../mdx/periodstodate-mdx.md) , где свойство Type иерархии атрибута, на котором основан уровень, имеет значение *years*. Таким образом, вызов `Ytd(Member_Expression)` эквивалентен вызову `PeriodsToDate(Year_Level_Expression,Member_Expression)`. Обратите внимание, что эта функция не будет работать, если свойство Type имеет значение *FiscalYears*.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается сумма `Measures.[Order Quantity]` элемента, агрегированная за первые восемь месяцев 2003 календарного года, которые содержатся в `Date` измерении, из куба **Adventure Works** .  
  
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
  
 **YTD** часто используется в сочетании без заданных параметров, что означает, что функция [CurrentMember &#40;многомерных выражений&#41;](../mdx/currentmember-mdx.md) будет отображать в отчете выполняющийся совокупный итог с начала года, как показано в следующем запросе:  
  
 `WITH MEMBER MEASURES.YTDDEMO AS`  
  
 `AGGREGATE(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDDEMO} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
