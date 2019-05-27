---
title: Создание, областью действия запроса именованных наборов (многомерные Выражения) с | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- query-scoped named sets [MDX]
- WITH keyword
ms.assetid: 78bc1e9a-1bc4-4a5a-ab0b-cf430c8fbfe1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a611d3d20d269bb9c3fa3a1f764181b1660713b0
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66074070"
---
# <a name="creating-query-scoped-named-sets-mdx"></a>Создание именованных наборов с областью действия запроса (многомерные выражения)
  Если именованный набор нужен только в одном запросе многомерных выражений, этот набор можно определить с помощью ключевого слова WITH. Именованный набор, созданный с использованием ключевого слова WITH, уничтожается после выполнения запроса.  
  
 Как уже обсуждалось в этом разделе, ключевое слово WITH имеет достаточно гибкую функциональность и даже позволяет использовать функции для определения именованного набора.  
  
> [!NOTE]  
>  Дополнительные сведения об именованных наборах см. в разделе [Построение именованных наборов в многомерных выражениях](mdx-named-sets-building-named-sets.md).  
  
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
 В следующем запросе многомерных выражений извлекаются сведения о продажах вин Шардоне и Шабли из образца базы данных `FoodMart 2000` для служб Microsoft SQL Server 2000 Analysis Services. Этот запрос возвращает достаточно простой результирующий набор, однако является очень длинным и громоздким с точки зрения его обслуживания.  
  
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
  
 Например, в следующем запросе многомерных выражений для создания именованного набора [используются функции многомерных выражений](/sql/mdx/filter-mdx)Filter [,](/sql/mdx/current-mdx)CurrentMember [и](/sql/mdx/members-string-mdx) Name `[ChardonnayChablis]` и функция языка VBA InStr. Эта версия именованного набора `[ChardonnayChablis]` идентична явно определенному набору, показанному ранее в этом разделе.  
  
```  
WITH SET [ChardonnayChablis] AS  
   'Filter([Product].Members, (InStr(1, [Product].CurrentMember.Name, "chardonnay") <> 0) OR (InStr(1, [Product].CurrentMember.Name, "chablis") <> 0))'  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
  
```  
  
## <a name="see-also"></a>См. также  
 [Инструкция SELECT (многомерные выражения)](/sql/mdx/mdx-data-manipulation-select)   
 [Создание именованных наборов с областью действия сеанса (многомерные выражения)](mdx-named-sets-creating-session-scoped-named-sets.md)  
  
  
