---
title: Count (уровни иерархии) (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cc09cf02cb0ee75788cbd2e6ff9e9d99ab34e784
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577576"
---
# <a name="count-hierarchy-levels-mdx"></a>Count (уровни иерархии) (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [Число &#40;задать&#41; &#40;многомерных Выражений&#41;](../mdx/count-set-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
