---
title: Непустая (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 45daf970f69322cad36bbe5419bf1dc8cc8009b9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088346"
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
  
## <a name="remarks"></a>Remarks  
 Эта функция возвращает непустые кортежи из первого заданного кортежа, полученные с учетом кортежей второго набора. Функция **непустого** учета учитывает вычисления и сохраняет дубликаты кортежей. Если второй набор не предоставлен, выражение рассматривается в контексте текущих координат элементов иерархий атрибута и мер в кубе.  
  
> [!NOTE]  
>  Используйте эту функцию вместо устаревшей функции [NonEmptyCrossjoin &#40;многомерных выражений&#41;](../mdx/nonemptycrossjoin-mdx.md) .  
  
> [!IMPORTANT]  
>  Непустота — характеристика ячеек, на которые ссылаются кортежи, а не самих кортежей.  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показан простой пример **непустого**значения, в котором возвращаются все клиенты, у которых значение, отличное от NULL, для объема продаж через Интернет, равное 1 июля 2001:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `, {([Date].[Calendar].[Date].&[20010701], [Measures].[Internet Sales Amount])}`  
  
 `)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 В следующем примере возвращается набор кортежей, содержащих заказчиков и даты покупки, с использованием функции **Filter** и **непустых** функций для поиска последней даты покупки каждым клиентом:  
  
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
  
## <a name="see-also"></a>См. также:  
 [&#40;&#41;многомерных выражений DefaultMember](../mdx/defaultmember-mdx.md)   
 [Фильтрация &#40;&#41;многомерных выражений](../mdx/filter-mdx.md)   
 [&#40;&#41;многомерных выражений](../mdx/isempty-mdx.md)   
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)   
 [NonEmptyCrossjoin &#40;&#41;многомерных выражений](../mdx/nonemptycrossjoin-mdx.md)  
  
  
