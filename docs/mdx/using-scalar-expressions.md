---
title: Использование скалярных выражений | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b87fad1b9c568f4ebd5f65ef3705001b12d26693
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038039"
---
# <a name="using-scalar-expressions"></a>Использование скалярных выражений


  В многомерных выражениях скалярное выражение является элементом синтаксиса многомерных выражений, при вычислении которого возвращается единственное в контексте вычисления значение.  
  
 К скалярным относятся выражения строкового, числового и календарного типа в многомерных выражениях.  
  
 Скалярные выражения обычно используются в определениях вычисляемых элементов, так как вычисляемые элементы должны возвращать скалярное значение. В следующем запросе показаны примеры вычисляемых элементов в измерении мер, в которых используются различные типы скалярного выражения:  
  
 `WITH`  
  
 `MEMBER MEASURES.NumericValue AS 10`  
  
 `MEMBER MEASURES.NumericExpression AS 10 + 10`  
  
 `MEMBER MEASURES.NumericExpressionBasedOnMeasure AS [Measures].[Internet Sales Amount] + 10`  
  
 `MEMBER MEASURES.StringValue AS "10"`  
  
 `MEMBER MEASURES.ConcatenatedString AS "10" + "10"`  
  
 `MEMBER MEASURES.StringFunction AS MEASURES.CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.TodaysDate AS NOW()`  
  
 `SELECT`  
  
 `{MEASURES.NumericValue,MEASURES.NumericExpression,MEASURES.NumericExpressionBasedOnMeasure,`  
  
 `MEASURES.StringValue, MEASURES.ConcatenatedString, MEASURES.StringFunction, MEASURES.TodaysDate}`  
  
 `ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 Единственный тип данных, который может быть возвращен вычисляемой или иной мерой — тип OLE Variant. Поэтому иногда требуется привести значение меры к определенному типу, чтобы обеспечить ожидаемое поведение. Пример этого приведен в следующем запросе:  
  
```  
WITH  
//Two calculated measures that return strings  
MEMBER MEASURES.NumericString1 AS "10"  
MEMBER MEASURES.NumericString2 AS "10"  
//In this case, the + operator acts to concatenate the strings  
MEMBER MEASURES.Concatenation AS MEASURES.NumericString1 + MEASURES.NumericString2  
//Casting one value to an integer with the CINT function causes the second measure  
//to be treated as an integer too, so that the + operator now acts to add the values  
MEMBER MEASURES.Addition AS CINT(MEASURES.NumericString1) + MEASURES.NumericString2  
SELECT  
{MEASURES.NumericString1,MEASURES.NumericString2,MEASURES.Concatenation,MEASURES.Addition }  
ON COLUMNS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения &#40;&#41;многомерных выражений](../mdx/expressions-mdx.md)  
  
  
