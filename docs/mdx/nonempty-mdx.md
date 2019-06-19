---
title: NonEmpty (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 91e6d478397cf9fa77a6ca33748b5a4515034471
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63278519"
---
# <a name="nonempty-mdx"></a>NonEmpty (многомерные выражения)


  Возвращает набор непустых кортежей из заданного набора, основываясь на прямом произведении заданного набора со вторым набором.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NONEMPTY(set_expression1 [,set_expression2])  
```  
  
## <a name="arguments"></a>Аргументы  
 *set_expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *set_expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Примечания  
 Эта функция возвращает непустые кортежи из первого заданного кортежа, полученные с учетом кортежей второго набора. **NonEmpty** функция принимает вычисления и сохраняет повторяющиеся кортежи. Если второй набор не предоставлен, выражение рассматривается в контексте текущих координат элементов иерархий атрибута и мер в кубе.  
  
> [!NOTE]  
>  Используйте эту функцию, а не устаревший [NonEmptyCrossjoin &#40;многомерных Выражений&#41; ](../mdx/nonemptycrossjoin-mdx.md) функции.  
  
> [!IMPORTANT]  
>  Непустота — характеристика ячеек, на которые ссылаются кортежи, а не самих кортежей.  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показано является простым примером **NonEmpty**, возвращающей всех заказчиков, имеющих значение отличное от null для Internet Sales Amount 1 июля 2001 года:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `, {([Date].[Calendar].[Date].&[20010701], [Measures].[Internet Sales Amount])}`  
  
 `)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 В следующем примере возвращается набор кортежей, включающий заказчиков и даты покупки **фильтра** функции и **NonEmpty** функции для поиска последней датой каждого заказчика покупку:  
  
 `WITH SET MYROWS AS FILTER`  
  
 `(NONEMPTY`  
  
 `([Customer].[Customer Geography].[Customer].MEMBERS`  
  
 `* [Date].[Date].[Date].MEMBERS`  
  
 `, [Measures].[Internet Sales Amount]`  
  
 `) AS MYSET`  
  
 `, NOT(MYSET.CURRENT.ITEM(0)`  
  
 `IS MYSET.ITEM(RANK(MYSET.CURRENT, MYSET)).ITEM(0))`  
  
 `)`  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `MYROWS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [DefaultMember &#40;многомерных Выражений&#41;](../mdx/defaultmember-mdx.md)   
 [Filter (многомерные выражения)](../mdx/filter-mdx.md)   
 [IsEmpty &#40;многомерных Выражений&#41;](../mdx/isempty-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)   
 [NonEmptyCrossjoin &#40;многомерных Выражений&#41;](../mdx/nonemptycrossjoin-mdx.md)  
  
  
