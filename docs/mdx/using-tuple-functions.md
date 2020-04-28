---
title: Использование функций кортежей | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9a329c8786ce580469e4601709509ca8a2de73f6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68037977"
---
# <a name="using-tuple-functions"></a>Функции кортежей


  Функции кортежей извлекают кортежи либо из набора, либо путем разрешения строкового представления кортежа.  
  
 Функции кортежей, подобно функциям элементов и функциям наборов, важны для согласования многомерных структур, обнаруженных в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 В многомерных выражениях есть три функции кортежей, [&#40;&#41;многомерных выражений ](../mdx/current-mdx.md), [элемент &#40;кортеж&#41; &#40;MDX&#41;](../mdx/item-tuple-mdx.md) и [StrToTuple &#40;MDX ](../mdx/strtotuple-mdx.md)&#41;. Следующий пример запроса демонстрирует использование каждой из них:  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of Years and Countries`  
  
 `SET MyTuples AS  [Date].[Calendar Year].[Calendar Year].MEMBERS * [Customer].[Country].[Country].MEMBERS`  
  
 `//Returns a string representation of that set using the Current and Generate functions`  
  
 `MEMBER MEASURES.CURRENTDEMO AS GENERATE(MyTuples, TUPLETOSTR(MyTuples.CURRENT), ", ")`  
  
 `//Retrieves the fourth tuple from that set and displays it as a string`  
  
 `MEMBER MEASURES.ITEMDEMO AS TUPLETOSTR(MyTuples.ITEM(3))`  
  
 `//Creates a tuple consisting of the measure Internet Sales Amount and the country Australia from a string`  
  
 `MEMBER MEASURES.STRTOTUPLEDEMO AS STRTOTUPLE("([Measures].[Internet Sales Amount]" + ", [Customer].[Country].&[Australia])")`  
  
 `SELECT{MEASURES.CURRENTDEMO,MEASURES.ITEMDEMO,MEASURES.STRTOTUPLEDEMO} ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Функции &#40;синтаксиса многомерных выражений&#41;](../mdx/functions-mdx-syntax.md)   
 [Использование функций элементов](../mdx/using-member-functions.md)   
 [Функции наборов](../mdx/using-set-functions.md)  
  
  
