---
title: NonEmpty (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4a718a7e75a9b31b7d35cdc33883c97739aee68c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580286"
---
# <a name="nonempty-mdx"></a>NonEmpty (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор непустых кортежей из заданного набора, основываясь на прямом произведении заданного набора со вторым набором.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NONEMPTY(set_expression1 [,set_expression2])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *set_expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Примечания  
 Эта функция возвращает непустые кортежи из первого заданного кортежа, полученные с учетом кортежей второго набора. **NonEmpty** функция отслеживает вычисления и сохраняет повторяющиеся кортежи. Если второй набор не предоставлен, выражение рассматривается в контексте текущих координат элементов иерархий атрибута и мер в кубе.  
  
> [!NOTE]  
>  Используйте эту функцию, а не устаревшие [NonEmptyCrossjoin &#40;многомерных Выражений&#41; ](../mdx/nonemptycrossjoin-mdx.md) функции.  
  
> [!IMPORTANT]  
>  Непустота — характеристика ячеек, на которые ссылаются кортежи, а не самих кортежей.  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показано простой пример **NonEmpty**, возвращающей всех заказчиков, которые имели непустое значение для Internet Sales Amount 1 июля 2001 года:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `, {([Date].[Calendar].[Date].&[20010701], [Measures].[Internet Sales Amount])}`  
  
 `)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 В следующем примере возвращается набор кортежей, включающий заказчиков и даты покупки **фильтра** функции и **NonEmpty** функции для поиска даты последней покупки, каждого заказчика:  
  
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
 [Фильтр &#40;многомерных Выражений&#41;](../mdx/filter-mdx.md)   
 [IsEmpty &#40;многомерных Выражений&#41;](../mdx/isempty-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)   
 [NonEmptyCrossjoin &#40;многомерных Выражений&#41;](../mdx/nonemptycrossjoin-mdx.md)  
  
  
