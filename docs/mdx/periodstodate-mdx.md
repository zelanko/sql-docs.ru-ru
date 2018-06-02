---
title: PeriodsToDate (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9d5e15800ed0f7118e14a90d7879faa5cef9bcd7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580896"
---
# <a name="periodstodate-mdx"></a>PeriodsToDate (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор элементов с общим родителем, находящихся на том же уровне, что и данный элемент, начиная с первого такого элемента и заканчивая данным элементом, в соответствии с ограничениями заданного уровня в измерении Time.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PeriodsToDate( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 В области действия заданного уровня **PeriodsToDate** функция возвращает набор периодов на том же уровне, что и указанный элемент, начиная с первого периода и заканчивая указанным элементом.  
  
-   Если уровень указан, текущий элемент иерархии определяется *иерархии*. **CurrentMember**, где *иерархии*является иерархией указанного уровня.  
  
-   Если не указан ни уровень, ни элемент, то уровнем становится родительский уровень текущего элемента первой иерархии первого измерения типа Time в группе мер.  
  
 Функция `PeriodsToDate( Level_Expression, Member_Expression )` функционально эквивалентна следующему многомерному выражению:  
  
 `TopCount(Descendants(Ancestor(Member_Expression, Level_Expression), Member_Expression.Level), 1):Member_Expression`  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается сумма `Measures.[Order Quantity]` член, суммарный за первые восемь месяцев календарного 2003, содержащихся в `Date` измерения, от **Adventure Works** куба.  
  
```  
WITH MEMBER [Date].[Calendar].[First8Months2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Year],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First8Months2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 В следующем примере выполняются статистические вычисления за первые два месяца второго полугодия 2003 календарного года.  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Semester],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First2MonthsSecondSemester2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
## <a name="see-also"></a>См. также  
 [TopCount &#40;многомерных Выражений&#41;](../mdx/topcount-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
