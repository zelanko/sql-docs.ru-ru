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
manager: kfile
ms.openlocfilehash: 1c9979b6b9fcb04115695cbe8d9c224e1c6c1f57
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63251594"
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
  
  
