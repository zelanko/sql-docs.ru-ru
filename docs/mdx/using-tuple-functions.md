---
title: Функции кортежей | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a58be5cbd0ea4101f5be2ebb8e29c1669d7f09f4
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581636"
---
# <a name="using-tuple-functions"></a>Функции кортежей
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Функции кортежей извлекают кортежи либо из набора, либо путем разрешения строкового представления кортежа.  
  
 Функции кортежей, подобно функциям элементов и функциям наборов, важны для согласования многомерных структур, обнаруженных в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 В многомерных Выражениях существуют три функции кортежей [текущей &#40;многомерных Выражений&#41;](../mdx/current-mdx.md), [элемент &#40;кортежа&#41; &#40;многомерных Выражений&#41; ](../mdx/item-tuple-mdx.md) и [StrToTuple &#40;&#41;](../mdx/strtotuple-mdx.md). Следующий пример запроса демонстрирует использование каждой из них:  
  
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
  
## <a name="see-also"></a>См. также  
 [Функции &#40;синтаксис многомерных Выражений&#41;](../mdx/functions-mdx-syntax.md)   
 [С помощью функции-члены](../mdx/using-member-functions.md)   
 [Использование функций наборов](../mdx/using-set-functions.md)  
  
  
