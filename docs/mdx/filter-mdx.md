---
title: Filter (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d740148052712a69a39e0de314496733b3b26a8b
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740533"
---
# <a name="filter-mdx"></a>Filter (многомерные выражения)


  Возвращает набор, получающийся в результате фильтрации заданного набора на основе условия поиска.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Filter(Set_Expression, Logical_Expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Logical_Expression*  
 Допустимое многомерное выражение иерархии, принимающее значение «true» или «false».  
  
## <a name="remarks"></a>Примечания  
 **Фильтра** функция вычисляет указанное логическое выражение для каждого кортежа в указанном наборе. Функция возвращает набор, состоящий из всех кортежей указанного набора, где логическое выражение принимает значение **true**. Если ни для каких кортежей принимают значение **true**, возвращается пустой набор.  
  
 **Фильтра** функция работает таким образом, аналогичны [IIf](../mdx/iif-mdx.md) функции. **IIf** функция возвращает только один из двух вариантов на основе вычисления логического Многомерного выражения, а **фильтра** функция возвращает набор кортежей, удовлетворяющих заданному условию поиска. В результате **фильтра** функция выполняет `IIf(Logical_Expression, Set_Expression.Current, NULL)` для каждого кортежа набора и возвращает результирующий набор.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано использование функции Filter на оси строк запроса, чтобы получить только даты, когда мера «Продажи через Интернет — сумма продаж» больше 10 000 долларов США:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `FILTER(`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `,  [Measures].[Internet Sales Amount]>10000)`  
  
 `ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 Функция Filter может также использоваться в определениях вычисляемых элементов. В следующем примере возвращается сумма `Measures.[Order Quantity]` член, суммарный за первые девять месяцев 2003, содержащихся в `Date` измерения, от **Adventure Works** куба. **PeriodsToDate** функции определяются кортежи в наборе, по которому **статистические** работает. **Фильтра** функция ограничивает возвращаемые имеющих более низкие значения для меры Reseller Sales Amount за предыдущий период времени.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
