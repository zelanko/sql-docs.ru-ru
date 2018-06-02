---
title: Измерения (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: af73d6f08432a63a207c06d361354d6e45b6a07d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577936"
---
# <a name="dimension-mdx"></a>Dimension (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает иерархию, содержащую заданный элемент, уровень или иерархию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.Dimension  
  
Level syntax  
Level_Expression.Dimension  
  
Member syntax  
Member_Expression.Dimension  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
### <a name="examples"></a>Примеры  
 В следующем примере используется **измерения** функции вместе с **имя** возвращается имя иерархии указанного элемента.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Name  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 В следующем примере при помощи функций Dimension, Levels и Count возвращается количество уровней в иерархии, содержащей указанный элемент.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 В следующем примере используется **измерения** функции вместе с **элементы** и **число** возвращается количество элементов в иерархии, содержащей указанный элемент.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Число &#40;уровней иерархии&#41; &#40;многомерных Выражений&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Число &#40;задать&#41; &#40;многомерных Выражений&#41;](../mdx/count-set-mdx.md)   
 [Уровни &#40;многомерных Выражений&#41;](../mdx/levels-mdx.md)   
 [Члены &#40;задать&#41; &#40;многомерных Выражений&#41;](../mdx/members-set-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
