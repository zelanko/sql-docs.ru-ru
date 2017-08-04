---
title: "IIf (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IIF
dev_langs:
- kbMDX
helpviewer_keywords:
- IIf function
ms.assetid: ec7b35e6-f4c5-40bf-93c8-b83c1cc26fe2
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0b520aa3c3761c8dd8452b1732923b7415bcbca6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="iif-mdx"></a>IIf (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вычисляет выражения различных ветвей в зависимости от значения логического условия — true или false.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IIf(Logical_Expression, Expression1 [HINT <hints>], Expression2 [HINT <hints>])  
```  
  
## <a name="arguments"></a>Аргументы  
 Функция IIf принимает три аргумента: iif (\<условие >, \<then ветвь >, \<else ветвь >).  
  
 *Logical_Expression*  
 Условие, результатом которого является **true** (1) или **false** (0). Должно быть допустимым логическим многомерным выражением.  
  
 *Указание expression1 [Eager | Strict | Отложенная]]*  
 Используется, если логическое выражение принимает значение **true**. Expression1 должно быть допустимым логическим многомерным выражением.  
  
 *Указание Expression2 [Eager | Strict | Отложенная]]*  
 Используется, если логическое выражение принимает значение **false**. Expression2 должно быть допустимым логическим многомерным выражением.  
  
## <a name="remarks"></a>Замечания  
 Условие, заданное логическое выражение, результатом которого является **false** когда значение этого выражения равно нулю. Любое другое значение, результатом которого является **true**.  
  
 Если условие равно **true**, **IIf** функция возвращает первое выражение. В противном случае функция возвращает второе выражение.  
  
 Заданные выражения могут возвращать значения или объекты многомерных выражений. Более того, типы этих выражений не должны обязательно совпадать.  
  
 **IIf** функция не рекомендуется для создания набора элементов на основе критерия поиска. Вместо этого используйте [фильтра](../mdx/filter-mdx.md) функции для вычисления каждого элемента заданного набора по логическому критерию и возврата подмножества элементов.  
  
> [!NOTE]  
>  Если любое из выражений возвращает значение NULL, результирующий набор будет содержать значение NULL, если будет выполнено условие, соответствующее этому выражению.  
  
 Hint — необязательный модификатор, определяющий, как и когда вычисляется выражение. Оно позволяет переопределить план запроса по умолчанию, указав, как вычисляется выражение.  
  
-   EAGER вычисляет выражения на исходном подпространстве IIF.  
  
-   STRICT вычисляет выражение только в ограниченном подпространстве, созданном логическим условным выражением.  
  
-   LAZY позволяет вычислять выражение в режиме «ячейка за ячейкой».  
  
 Указания EAGER и STRICT применяются только к ветви THEN-ELSE IIF, но LAZY применяется ко всем многомерным выражениям. За любым многомерным выражением может следовать HINT LAZY, что приведет к вычислению выражения в режиме «ячейка за ячейкой».  
  
 Указания EAGER и STRICT являются взаимоисключающими: их можно использовать в одной функции IIF(,,), только в разных выражениях.  
  
 Дополнительные сведения см. в разделе [указания запросов функции IIF в SQL Server Analysis Services 2008](http://go.microsoft.com/fwlink/?LinkId=269540) и [планы выполнения и указания плана для функции IIF многомерного Выражения и инструкции CASE](http://go.microsoft.com/fwlink/?LinkId=269565).  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показано простое использование **IIF** внутри вычисляемой меры на возвращать одно из двух разных строковых значений, если меру Internet Sales Amount больше или меньше 10 000 долларов США:  
  
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
  
 Ниже приведен пример **IIF** возвращения одного из двух наборов в функции Generate, чтобы создать сложный набор кортежей по строкам:  
  
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
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

