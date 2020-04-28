---
title: Filter (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3a70bceed4cdccf6a22f0cfea4e5093634f88f1f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68132690"
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
  
## <a name="remarks"></a>Remarks  
 Функция **Filter** вычисляет указанное логическое выражение для каждого кортежа в указанном наборе. Функция возвращает набор, состоящий из каждого кортежа в указанном наборе, где логическое выражение принимает **значение true**. Если ни один из кортежей не имеет значения **true**, возвращается пустой набор.  
  
 Функция **Filter** работает аналогично функции [IIf](../mdx/iif-mdx.md) . Функция **IIf** возвращает только один из двух параметров на основе вычисления логического выражения многомерных выражений, а функция **Filter** возвращает набор кортежей, соответствующих указанному условию поиска. Фактически функция **Filter** выполняется `IIf(Logical_Expression, Set_Expression.Current, NULL)` для каждого кортежа в наборе и возвращает результирующий набор.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано использование функции Filter на оси строк запроса, чтобы получить только даты, когда мера «Продажи через Интернет — сумма продаж» больше 10 000 долларов США:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `FILTER(`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `,  [Measures].[Internet Sales Amount]>10000)`  
  
 `ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 Функция Filter может также использоваться в определениях вычисляемых элементов. В следующем примере возвращается сумма `Measures.[Order Quantity]` элемента, агрегированная за первые девять месяцев 2003, содержащихся в `Date` измерении, из куба **Adventure Works** . Функция **PeriodsToDate** определяет кортежи в наборе, для которого работает **агрегатная** функция. Функция **Filter** ограничивает возвращаемые кортежи значениями, которые имеют меньшие значения для меры Товарооборот посредников за предыдущий период времени.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
