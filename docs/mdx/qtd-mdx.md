---
description: Qtd (многомерные выражения)
title: Текущему кварталу (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ea3bd80fa85d95dd3adf52793d5895425b40b9fe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500457"
---
# <a name="qtd-mdx"></a>Qtd (многомерные выражения)


  Возвращает набор элементов с общим родителем, находящиеся на том же уровне, что и заданный элемент, начиная с первого элемента того же уровня и заканчивая данным элементом, в соответствии с ограничением уровня *квартала* в измерении времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Qtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Комментарии  
 Если выражение элемента не указано, по умолчанию используется текущий элемент первой иерархии с уровнем *кварталов* в первом измерении типа *time* в группе мер.  
  
 Функция **текущему кварталу** является сочетанием клавиш для функции [PeriodsToDate &#40;многомерных выражений&#41;](../mdx/periodstodate-mdx.md) , для аргумента Expression уровня которого задано значение *Quarter*. Таким образом, выражение `Qtd(Member_Expression)` равнозначно выражению `PeriodsToDate(Quarter_Level_Expression, Member_Expression)`.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается сумма `Measures.[Order Quantity]` элемента, агрегированная за первые два месяца третьего квартала календарного года 2003, которые содержатся в `Date` измерении, из куба **Adventure Works** .  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        QTD([Date].[Calendar].[Month].[August 2003])  
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
