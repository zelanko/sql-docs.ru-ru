---
title: Использование логических функций | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 723d481bc858d7d1db4a63cbb32ab5614eddbb55
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097172"
---
# <a name="using-logical-functions"></a>Использование логических функций


  Логическая функция выполняет логическую операцию или сравнение объектов и выражений, результатом вычисления логической функции будет логическое значение. В многомерных выражениях логические функции крайне важны для определения положения элементов.  
  
 Наиболее часто используемые Логическая функция — это **IsEmpty** функции. Дополнительные сведения об использовании **IsEmpty** функции, см. в разделе [работа с пустыми значениями](../mdx/working-with-empty-values.md).  
  
 Следующий запрос показывает, как использовать **IsLeaf** и **IsAncestor** функции:  
  
 `WITH`  
  
 `//Returns true if the CurrentMember on Calendar is a leaf member, ie it has no children`  
  
 `MEMBER MEASURES.[IsLeafDemo] AS IsLeaf([Date].[Calendar].CurrentMember)`  
  
 `//Returns true if the CurrentMember on Calendar is an Ancestor of July 1st 2001`  
  
 `MEMBER MEASURES.[IsAncestorDemo] AS IsAncestor([Date].[Calendar].CurrentMember, [Date].[Calendar].[Date].&[1])`  
  
 `SELECT{MEASURES.[IsLeafDemo],MEASURES.[IsAncestorDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;синтаксис многомерных Выражений&#41;](../mdx/functions-mdx-syntax.md)  
  
  
