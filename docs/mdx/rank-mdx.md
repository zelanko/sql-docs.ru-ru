---
title: "Rank (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RANK
dev_langs: kbMDX
helpviewer_keywords: Rank function [MDX]
ms.assetid: 3cea35ed-57c4-4b47-a736-cee00275509b
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ba556f2a298ea65ff2d9662a8deba90334d31a0f
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="rank-mdx"></a>Rank (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Замечания  
 Если числовое выражение указано, **ранг** функция определяет ранг заданного кортежа, оценивая указанное числовое выражение над кортежем. Если числовое выражение указано, **ранг** функция тот же ранг присваивает всем кортежам с повторяющимися значениями в наборе. Присваивание одинакового ранга кортежам с повторяющимися значениями изменяет ранги последующих кортежей набора. Например, пусть набор состоит из кортежей `{(a,b), (e,f), (c,d)}`. Значение кортежа `(a,b)` совпадает со значением `(c,d)`. Если кортеж `(a,b)` имеет ранг 1, тогда и `(a,b)`, и `(c,d)` будут иметь ранг 1. Однако кортеж `(e,f)` будет иметь ранг 3. В этом наборе не может быть кортежей с рангом 2.  
  
 Если числовое выражение не указано, **ранг** функция возвращает порядковый номер указанного кортежа.  
  
 **Ранг** функция не упорядочивает набор.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается набор кортежей, включающий заказчиков и даты, с помощью **фильтра**, **NonEmpty**, **элемент**, и **ранг** функции для поиска даты последней покупки, каждого заказчика.  
  
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
  
 В следующем примере используется **порядок** функции, а не **ранг** функции для упорядочивания элементов иерархии City на основе меры Reseller Sales Amount и затем отображает их в упорядоченном виде. С помощью **порядок** функции для упорядочивания набора элементов иерархии City, сортировка выполняется только один раз и затем линейный просмотр перед его доставкой в отсортированном порядке.  
  
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
 [Порядок &#40; Многомерные Выражения &#41;](../mdx/order-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
