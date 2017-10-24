---
title: "Создание областью действия запроса именованных наборов (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- query-scoped named sets [MDX]
- WITH keyword
ms.assetid: 78bc1e9a-1bc4-4a5a-ab0b-cf430c8fbfe1
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 06751ad71a12e537728167d4d8a9cdec0a870962
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-named-sets---creating-query-scoped-named-sets"></a>Именованные наборы - Создание областью действия запроса многомерных Выражений именованных наборов
  Если именованный набор нужен только в одном запросе многомерных выражений, этот набор можно определить с помощью ключевого слова WITH. Именованный набор, созданный с использованием ключевого слова WITH, уничтожается после выполнения запроса.  
  
 Как уже обсуждалось в этом разделе, ключевое слово WITH имеет достаточно гибкую функциональность и даже позволяет использовать функции для определения именованного набора.  
  
> [!NOTE]  
>  Дополнительные сведения об именованных наборах см. в разделе [Построение именованных наборов в многомерных выражениях](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md).  
  
## <a name="with-keyword-syntax"></a>Синтаксис ключевого слова WITH  
 Чтобы указать ключевое слово WITH в инструкции SELECT многомерного выражения, используется следующий синтаксис:  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ]   
SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]  
FROM <SELECT subcube clause>   
[ <SELECT slicer axis clause> ]  
[ <SELECT cell property list clause> ]  
  
<SELECT WITH clause> ::=  
   ( SET Set_Identifier AS 'Set_Expression')  
  
```  
  
 В синтаксисе с ключевым словом WITH параметр `Set_Identifier` — это псевдоним именованного набора. Параметр `Set_Expression` содержит выражение набора, на который ссылается псевдоним именованного набора.  
  
## <a name="with-keyword-example"></a>Пример использования ключевого слова WITH  
 В следующем запросе многомерных выражений извлекаются сведения о продажах вин Шардоне и Шабли из образца базы данных **FoodMart 2000**для служб Microsoft SQL Server 2000 Analysis Services. Этот запрос возвращает достаточно простой результирующий набор, однако является очень длинным и громоздким с точки зрения его обслуживания.  
  
```  
SELECT  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]} ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
 Чтобы упростить обслуживание предыдущего запроса многомерных выражений, с помощью ключевого слова WITH можно создать именованный набор. В следующем примере показано, как создать именованный набор `[ChardonnayChablis]`при помощи ключевого слова WITH, делая инструкцию SELECT короче и проще.  
  
```  
WITH SET [ChardonnayChablis] AS  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]}  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
### <a name="using-functions-together-with-the-with-keyword"></a>Использование функций с ключевым словом WITH  
 Хотя можно явно определять каждый элемент именованного набора, при таком подходе инструкция получается слишком длинной. Чтобы упростить создание и обслуживание именованного набора, для определения элементов используются функции многомерных выражений.  
  
 Например, в следующем запросе многомерных выражений для создания именованного набора [используются функции многомерных выражений](../../../mdx/filter-mdx.md)Filter [,](../../../mdx/currentmember-mdx.md)CurrentMember [и](../../../mdx/name-mdx.md) Name `[ChardonnayChablis]` и функция языка VBA InStr. Эта версия именованного набора `[ChardonnayChablis]` идентична явно определенному набору, показанному ранее в этом разделе.  
  
```  
WITH SET [ChardonnayChablis] AS  
   'Filter([Product].Members, (InStr(1, [Product].CurrentMember.Name, "chardonnay") <> 0) OR (InStr(1, [Product].CurrentMember.Name, "chablis") <> 0))'  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
  
```  
  
## <a name="see-also"></a>См. также  
 [Инструкция SELECT (многомерные выражения)](../../../mdx/mdx-data-manipulation-select.md)   
 [Создание областью действия сеанса именованных наборов &#40; Многомерные Выражения &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-session-scoped-named-sets.md)  
  
  

