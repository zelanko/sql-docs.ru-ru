---
description: PeriodsToDate (многомерные выражения)
title: PeriodsToDate (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8b18fe4d90a8a0c56424c5e0a7f3607ceea0eae4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471706"
---
# <a name="periodstodate-mdx"></a>PeriodsToDate (многомерные выражения)


  Возвращает набор элементов с общим родителем, находящихся на том же уровне, что и данный элемент, начиная с первого такого элемента и заканчивая данным элементом, в соответствии с ограничениями заданного уровня в измерении Time.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PeriodsToDate( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Remarks  
 В пределах области указанного уровня функция **PeriodsToDate** возвращает набор периодов на том же уровне, что и указанный элемент, начиная с первого периода и заканчивая указанным элементом.  
  
-   Если уровень указан, текущий элемент иерархии является выводимой *иерархией*. **CurrentMember**, где *Иерархия*— это иерархия указанного уровня.  
  
-   Если не указан ни уровень, ни элемент, то уровнем становится родительский уровень текущего элемента первой иерархии первого измерения типа Time в группе мер.  
  
 Функция `PeriodsToDate( Level_Expression, Member_Expression )` функционально эквивалентна следующему многомерному выражению:  
  
 `TopCount(Descendants(Ancestor(Member_Expression, Level_Expression), Member_Expression.Level), 1):Member_Expression`  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается сумма `Measures.[Order Quantity]` элемента, агрегированная за первые восемь месяцев 2003 календарного года, которые содержатся в `Date` измерении, из куба **Adventure Works** .  
  
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
  
## <a name="see-also"></a>См. также:  
 [TopCount &#40;&#41;многомерных выражений ](../mdx/topcount-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
