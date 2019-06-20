---
title: Rank (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b1d234f02c8dfcd36073059210c1999cb95f5ab0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200663"
---
# <a name="rank-mdx"></a>Rank (многомерные выражения)


  Возвращает позицию, начиная с единицы, заданного кортежа в указанном множестве.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Rank(Tuple_Expression, Set_Expression [ ,Numeric Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Tuple_Expression*  
 Допустимое многомерное выражение, возвращающее кортеж.  
  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Примечания  
 Если числовое выражение указано, **ранг** функция определяет ранг заданного кортежа, оценивая указанное числовое выражение над кортежем. Если числовое выражение указано, **ранг** функция тот же ранг присваивает всем кортежам с повторяющимися значениями в наборе. Присваивание одинакового ранга кортежам с повторяющимися значениями изменяет ранги последующих кортежей набора. Например, пусть набор состоит из кортежей `{(a,b), (e,f), (c,d)}`. Значение кортежа `(a,b)` совпадает со значением `(c,d)`. Если кортеж `(a,b)` имеет ранг 1, тогда и `(a,b)`, и `(c,d)` будут иметь ранг 1. Однако кортеж `(e,f)` будет иметь ранг 3. В этом наборе не может быть кортежей с рангом 2.  
  
 Если числовое выражение не указано, **ранг** функция возвращает порядковый номер указанного кортежа.  
  
 **Ранг** функция упорядочивает набор.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается набор кортежей, включающий заказчиков и даты покупки с помощью **фильтра**, **NonEmpty**, **элемент**, и **ранг** функции для поиска последней датой каждого заказчика покупки.  
  
```  
WITH SET MYROWS AS FILTER  
   (NONEMPTY  
      ([Customer].[Customer Geography].MEMBERS  
         * [Date].[Date].[Date].MEMBERS  
         , [Measures].[Internet Sales Amount]  
      ) AS MYSET  
   , NOT(MYSET.CURRENT.ITEM(0)  
      IS MYSET.ITEM(RANK(MYSET.CURRENT, MYSET)).ITEM(0))  
   )  
SELECT [Measures].[Internet Sales Amount] ON 0,  
MYROWS ON 1  
FROM [Adventure Works]  
```  
  
 В следующем примере используется **порядок** функции, а не **ранг** функции, для упорядочивания элементов иерархии City на основе меры Reseller Sales Amount и затем отображает их в упорядоченном. С помощью **порядок** функцию в порядке старшинства набор элементов иерархии City, сортировка сделать только один раз и затем следуют линейный Просмотр, прежде чем представляемых в отсортированном порядке.  
  
```  
WITH   
SET OrderedCities AS Order  
   ([Geography].[City].[City].members  
   , [Measures].[Reseller Sales Amount], BDESC  
   )  
MEMBER [Measures].[City Rank] AS Rank  
   ([Geography].[City].CurrentMember, OrderedCities)  
SELECT {[Measures].[City Rank],[Measures].[Reseller Sales Amount]}  ON 0   
,Order  
   ([Geography].[City].[City].MEMBERS  
   ,[City Rank], ASC)  
    ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Порядок &#40;многомерных Выражений&#41;](../mdx/order-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
