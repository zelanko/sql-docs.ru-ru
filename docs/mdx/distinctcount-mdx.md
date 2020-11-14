---
description: DistinctCount (многомерные выражения)
title: DistinctCount (многомерные выражения) | Документация Майкрософт
ms.date: 11/12/2020
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 28807d1a24f97a6b197ad56d0434399ab53cd742
ms.sourcegitcommit: 54cd97a33f417432aa26b948b3fc4b71a5e9162b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2020
ms.locfileid: "94584851"
---
# <a name="distinctcount-mdx"></a>DistinctCount (многомерные выражения)


  Возвращает количество неодинаковых, непустых кортежей в наборе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DistinctCount(Set_Expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Комментарии  
 Функция **DistinctCount** эквивалентна `Count(Distinct(Set_Expression), EXCLUDEEMPTY)` .  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показано использование функции DistinctCount:  
  
 `WITH SET MySet AS`  
  
 `{[Customer].[Customer Geography].[Country].&[Australia],[Customer].[Customer Geography].[Country].&[Australia],`  
  
 `[Customer].[Customer Geography].[Country].&[Canada],[Customer].[Customer Geography].[Country].&[France],`  
  
 `[Customer].[Customer Geography].[Country].&[United Kingdom],[Customer].[Customer Geography].[Country].&[United Kingdom]}`  
  
 `*`  
  
 `{([Date].[Calendar].[Date].&[20010701],[Measures].[Internet Sales Amount] )}`  
  
 `//Returns the value 3 because Internet Sales Amount is null`  
  
 `//for the UK on the date specified`  
  
 `MEMBER MEASURES.SETDISTINCTCOUNT AS`  
  
 `DISTINCTCOUNT(MySet)`  
  
 `SELECT {MEASURES.SETDISTINCTCOUNT} ON 0`  
  
 `FROM [Adventure Works]`  
 
Функция DistinctCount возвращает различное количество элементов в наборе; в этом примере необязательный второй параметр используется для исключения элементов, которые не имеют значения для данного кортежа. В этом случае в наборе в первом параметре содержится четыре отдельных элемента, но функция возвращает три, так как только Австралия, Канада и Франция содержат данные за 1 июля 2001 для объема продаж через Интернет.
 
## <a name="see-also"></a>См. также:  
 [Count &#40;Set&#41; &#40;многомерных выражений&#41;](../mdx/count-set-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
