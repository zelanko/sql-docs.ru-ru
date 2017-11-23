---
title: "Создание областью действия запроса вычисляемых элементов (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WITH keyword
- query-scoped calculated members [MDX]
ms.assetid: c4507149-e67b-4e5d-9192-cc911acd9adc
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 8a621061e7b9b04dfea37443c631ae611ee031ab
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="mdx-calculated-members---query-scoped-calculated-members"></a>Многомерные Выражения вычисляемых элементов - вычисляемых элементов с областью действия запроса
  Если вычисляемый элемент используется только в одном многомерном запросе, его можно определить с помощью ключевого слова WITH. Вычисляемый элемент, созданный с помощью ключевого слова WITH, удаляется сразу после выполнения запроса.  
  
 Синтаксис ключевого слова WITH является достаточно гибким и позволяет создавать один вычисляемый элемент на основе другого.  
  
> [!NOTE]  
>  Дополнительные сведения о создании вычисляемых элементов см. в разделе [Создание вычисляемых элементов в многомерных выражениях (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-building-calculated-members.md).  
  
## <a name="with-keyword-syntax"></a>Синтаксис ключевого слова WITH  
 Для добавления ключевого слова WITH в инструкцию многомерных выражений SELECT используется следующий синтаксис.  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ] SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]FROM <SELECT subcube clause> [ <SELECT slicer axis clause> ][ <SELECT cell property list clause> ]  
<SELECT WITH clause> ::=  
   ( [ CALCULATED ] MEMBER <CREATE MEMBER body clause>) | <CREATE MEMBER body clause> ::= Member_Identifier AS 'MDX_Expression'  
   [ <CREATE MEMBER property clause> [ , <CREATE MEMBER property clause> ... ] ]  
<CREATE MEMBER property clause> ::=  
   ( MemberProperty_Identifier = Scalar_Expression )  
  
```  
  
 В синтаксисе ключевого слова WITH аргумент `Member_Identifier` — это полное имя вычисляемого элемента. Полное имя включает в себя измерение или уровень, с которым связан вычисляемый элемент. Аргумент `MDX_Expression` возвращает значение вычисляемого элемента после определения значения выражения. По желанию можно задать значения внутренних свойств ячейки для вычисляемого элемента, указав имя свойства ячейки в значении `MemberProperty_Identifier` , а значение свойства — в значении `Scalar_Expression` .  
  
## <a name="with-keyword-examples"></a>Примеры использования ключевого слова WITH  
 В следующем многомерном запросе определяется вычисляемый элемент `[Measures].[Special Discount]`, который рассчитывает особую скидку, исходя из начальной суммы скидки.  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 Вычисляемые элементы можно также создавать в любой точке иерархии. Например, в следующем многомерном запросе определяется вычисляемый элемент `[BigSeller]` для гипотетического куба продаж. С помощью этого вычисляемого элемента выясняется, продал ли заданный магазин хотя бы 100,00 бутылок пива и вина. Однако в запросе вычисляемый элемент `[BigSeller]` создается не как потомок измерения `[Product]` , а как потомок элемента `[Beer and Wine]` .  
  
```  
WITH   
   MEMBER [Product].[Beer and Wine].[BigSeller] AS  
  IIf([Product].[Beer and Wine] > 100, "Yes","No")  
SELECT  
   {[Product].[BigSeller]} ON COLUMNS,  
   Store.[Store Name].Members ON ROWS  
FROM Sales  
  
```  
  
 Вычисляемые элементы не обязательно должны зависеть только от существующих элементов куба. Вычисляемые элементы также могут создаваться на основе других вычисляемых элементов, определяемых в том же многомерном выражении. Например, в следующем многомерном запросе значение, созданное в первом вычисляемом элементе `[Measures].[Special Discount]`, используется для формирования значения второго вычисляемого элемента `[Measures].[Special Discounted Amount]`.  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Percentage] * 1.5,   
   FORMAT_STRING = 'Percent'  
  
   MEMBER [Measures].[Special Discounted Amount] AS  
   [Measures].[Reseller Average Unit Price] * [Measures].[Special Discount],   
   FORMAT_STRING = 'Currency'  
  
SELECT   
   {[Measures].[Special Discount], [Measures].[Special Discounted Amount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../../../mdx/mdx-function-reference-mdx.md)   
 [Инструкция SELECT (многомерные выражения)](../../../mdx/mdx-data-manipulation-select.md)   
 [Создание областью действия сеанса вычисляемые элементы &#40; Многомерные Выражения &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md)  
  
  
