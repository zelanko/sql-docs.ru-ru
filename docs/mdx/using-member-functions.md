---
title: С помощью функций-членов | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 54f600eb020472f93067f7b9fe1e867f2730d670
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097099"
---
# <a name="using-member-functions"></a>Использование функций элементов


  Функция элемента — это функция многомерного выражения, которая возвращает элемент. Функции элементов, подобно функциям кортежей и функциям наборов, необходимы для согласования многомерных структур, обнаруженных в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Множество функций-членов в многомерных Выражениях, наиболее важным является **CurrentMember** функцию, которая используется для определения текущего элемента в иерархии. Следующий запрос иллюстрирует, как использовать его, вместе с **родительского**, **предка**, и **Prevmember** функции:  
  
 `WITH`  
  
 `//Returns the name of the currentmember on the Calendar hierarchy`  
  
 `MEMBER MEASURES.[CurrentMemberDemo] AS [Date].[Calendar].CurrentMember.Name`  
  
 `//Returns the name of the parent of the currentmember on the Calendar hierarchy`  
  
 `MEMBER MEASURES.[ParentDemo] AS [Date].[Calendar].CurrentMember.Parent.Name`  
  
 `//Returns the name of the ancestor of the currentmember on the Calendar hierarchy at the Year level`  
  
 `MEMBER MEASURES.[AncestorDemo] AS ANCESTOR([Date].[Calendar].CurrentMember, [Date].[Calendar].[Calendar Year]).Name`  
  
 `//Returns the name of the member before the currentmember on the Calendar hierarchy`  
  
 `MEMBER MEASURES.[PrevMemberDemo] AS [Date].[Calendar].CurrentMember.Prevmember.Name`  
  
 `SELECT{MEASURES.[CurrentMemberDemo],MEASURES.[ParentDemo],MEASURES.[AncestorDemo],MEASURES.[PrevMemberDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;синтаксис многомерных Выражений&#41;](../mdx/functions-mdx-syntax.md)   
 [Функции кортежей](../mdx/using-tuple-functions.md)   
 [Использование функций наборов](../mdx/using-set-functions.md)  
  
  
