---
title: IIf (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 87b7b030776c1c18bb13307bf97db721fe472bd3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105327"
---
# <a name="iif-mdx"></a>IIf (многомерные выражения)


  Вычисляет выражения различных ветвей в зависимости от значения логического условия — true или false.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IIf(Logical_Expression, Expression1 [HINT <hints>], Expression2 [HINT <hints>])  
```  
  
## <a name="arguments"></a>Аргументы  
 Функция IIf принимает три аргумента: IIf (\<условие>, \<ветвь>, \<else>).  
  
 *Logical_Expression*  
 Условие, результатом которого является **значение true** (1) или **false** (0). Должно быть допустимым логическим многомерным выражением.  
  
 *Выражение1, подсказка [ Жесткое | Lazy]]*  
 Используется, когда логическое выражение принимает **значение true**. Expression1 должно быть допустимым логическим многомерным выражением.  
  
 *Указание expression2 [безотлагательная | Жесткое | Lazy]]*  
 Используется, когда логическое выражение принимает **значение false**. Expression2 должно быть допустимым логическим многомерным выражением.  
  
## <a name="remarks"></a>Remarks  
 Условие, заданное логическим выражением, возвращает **false** , если значение этого выражения равно нулю. Любое другое значение принимает значение **true**.  
  
 Если условие **истинно**, функция **IIf** возвращает первое выражение. В противном случае функция возвращает второе выражение.  
  
 Заданные выражения могут возвращать значения или объекты многомерных выражений. Более того, типы этих выражений не должны обязательно совпадать.  
  
 Функция **IIf** не рекомендуется для создания набора элементов на основе условий поиска. Вместо этого используйте функцию [Filter](../mdx/filter-mdx.md) для вычисления каждого элемента в указанном наборе по логическому выражению и возврата подмножества элементов.  
  
> [!NOTE]  
>  Если любое из выражений возвращает значение NULL, результирующий набор будет содержать значение NULL, если будет выполнено условие, соответствующее этому выражению.  
  
 Hint — необязательный модификатор, определяющий, как и когда вычисляется выражение. Оно позволяет переопределить план запроса по умолчанию, указав, как вычисляется выражение.  
  
-   EAGER вычисляет выражения на исходном подпространстве IIF.  
  
-   STRICT вычисляет выражение только в ограниченном подпространстве, созданном логическим условным выражением.  
  
-   LAZY позволяет вычислять выражение в режиме «ячейка за ячейкой».  
  
 Указания EAGER и STRICT применяются только к ветви THEN-ELSE IIF, но LAZY применяется ко всем многомерным выражениям. За любым многомерным выражением может следовать HINT LAZY, что приведет к вычислению выражения в режиме «ячейка за ячейкой».  
  
 Указания EAGER и STRICT являются взаимоисключающими: их можно использовать в одной функции IIF(,,), только в разных выражениях.  
  
 Дополнительные сведения см. [в разделе указания запросов функции IIf в SQL Server Analysis Services 2008](https://go.microsoft.com/fwlink/?LinkId=269540) и [планах выполнения и указания планов для функции многомерных выражений IIf и инструкции CASE](https://go.microsoft.com/fwlink/?LinkId=269565).  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показано простое использование **IIf** внутри вычисляемой меры для возврата одного из двух различных строковых значений, если мера продажи через Интернет превышает или меньше $10000:  
  
 `WITH MEMBER MEASURES.IIFDEMO AS`  
  
 `IIF([Measures].[Internet Sales Amount]>10000`  
  
 `, "Sales Are High", "Sales Are Low")`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.IIFDEMO} ON 0,`  
  
 `[Date].[Date].[Date].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Очень распространенное применение функции IIF — обработка ошибок «деления на ноль» в вычисляемых мерах, как в следующем примере:  
  
 `WITH`  
  
 `//Returns 1.#INF when the previous period contains no value`  
  
 `//but the current period does`  
  
 `MEMBER MEASURES.[Previous Period Growth With Errors] AS`  
  
 `([Measures].[Internet Sales Amount]-([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER))`  
  
 `/`  
  
 `([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER)`  
  
 `,FORMAT_STRING='PERCENT'`  
  
 `//Traps division by zero and returns null when the previous period contains`  
  
 `//no value but the current period does`  
  
 `MEMBER MEASURES.[Previous Period Growth] AS`  
  
 `IIF(([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER)=0,`  
  
 `NULL,`  
  
 `([Measures].[Internet Sales Amount]-([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER))`  
  
 `/`  
  
 `([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER)`  
  
 `),FORMAT_STRING='PERCENT'`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.[Previous Period Growth With Errors], MEASURES.[Previous Period Growth]} ON 0,`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004],`  
  
 `[Date].[Calendar].[Date])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Product].[Product Categories].[Subcategory].&[26])`  
  
 Ниже приведен пример использования **IIf** , возвращающего один из двух наборов внутри функции Generate для создания сложного набора кортежей в строках:  
  
 `SELECT {[Measures].[Internet Sales Amount]} ON 0,`  
  
 `//If Internet Sales Amount is zero or null`  
  
 `//returns the current year and the All Customers member`  
  
 `//else returns the current year broken down by Country`  
  
 `GENERATE(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS`  
  
 `, IIF([Measures].[Internet Sales Amount]=0,`  
  
 `{([Date].[Calendar Year].CURRENTMEMBER, [Customer].[Country].[All Customers])}`  
  
 `, {{[Date].[Calendar Year].CURRENTMEMBER} * [Customer].[Country].[Country].MEMBERS}`  
  
 `))`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Product].[Product Categories].[Subcategory].&[26])`  
  
 Наконец, этот пример иллюстрирует использование подсказок плана:  
  
 `WITH MEMBER MEASURES.X AS`  
  
 `IIF(`  
  
 `[Measures].[Internet Sales Amount]=0`  
  
 `, NULL`  
  
 `, (1/[Measures].[Internet Sales Amount]) HINT EAGER)`  
  
 `SELECT {[Measures].x} ON 0,`  
  
 `[Customer].[Customer Geography].[Country].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
