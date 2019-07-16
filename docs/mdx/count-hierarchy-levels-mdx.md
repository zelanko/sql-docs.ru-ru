---
title: Count (уровни иерархии) (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 17fe804de8bf2c20581ca5c00bee3a28dbce4d55
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68045199"
---
# <a name="count-hierarchy-levels-mdx"></a>Count (уровни иерархии) (многомерные выражения)


  Возвращает количество уровней в иерархии.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchy_Expression.Levels.Count  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
## <a name="remarks"></a>Примечания  
 Возвращает количество уровней иерархии, включая уровень `[All]`, если применимо.  
  
> [!IMPORTANT]  
>  Если измерение содержит единственную видимую иерархию, на нее можно сослаться по имени измерения или по имени иерархии, поскольку имя измерения разрешается в единственную видимую иерархию. Например, многомерное выражение `Measures.Levels.Count` является допустимым, поскольку измерение Measures разрешается в единственную видимую иерархию.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается количество уровней в пользовательской иерархии «Product Categories» куба «Adventure Works».  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Product Categories].Levels.Count   
Select Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Число &#40;измерения&#41; &#40;многомерных Выражений&#41;](../mdx/count-dimension-mdx.md)   
 [Число &#40;кортежа&#41; &#40;многомерных Выражений&#41;](../mdx/count-tuple-mdx.md)   
 [Count (наборы) (многомерные выражения)](../mdx/count-set-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
