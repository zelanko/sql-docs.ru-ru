---
title: Rank (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1081cacd0676f4eb0512780e9ddc7641edb99ca1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037068"
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
  
## <a name="remarks"></a>Remarks  
 Если числовое выражение указано, функция **Rank** определяет одномерный ранг для указанного кортежа, оценивая заданное числовое выражение с кортежем. Если числовое выражение указано, функция **Rank** присваивает один и тот же ранг кортежям с повторяющимися значениями в наборе. Присваивание одинакового ранга кортежам с повторяющимися значениями изменяет ранги последующих кортежей набора. Например, пусть набор состоит из кортежей `{(a,b), (e,f), (c,d)}`. Значение кортежа `(a,b)` совпадает со значением `(c,d)`. Если кортеж `(a,b)` имеет ранг 1, тогда и `(a,b)`, и `(c,d)` будут иметь ранг 1. Однако кортеж `(e,f)` будет иметь ранг 3. В этом наборе не может быть кортежей с рангом 2.  
  
 Если числовое выражение не указано, функция **Rank** возвращает порядковый номер указанного кортежа, отсчитываемый от единицы.  
  
 Функция **Rank** не упорядочивает набор.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается набор кортежей, содержащих заказчиков и даты покупки, с использованием функций **Filter**, **непустые**, **Item**и **Rank** для поиска последней даты покупки каждым клиентом.  
  
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
  
 В следующем примере функция **Order** , а не функция **Rank** , используется для ранжирования элементов иерархии City на основе меры Товарооборот посредников, а затем отображает их в порядке ранжирования. При использовании функции **Order** для предварительного упорядочения набора элементов иерархии City сортировка выполняется только один раз, а затем выполняется линейное сканирование, прежде чем будет представлен порядок сортировки.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Порядок &#40;&#41;многомерных выражений](../mdx/order-mdx.md)   
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
