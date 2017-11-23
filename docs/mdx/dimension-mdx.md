---
title: "Измерения (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Dimension
dev_langs: kbMDX
helpviewer_keywords: Dimension function
ms.assetid: 0e3ce539-1d34-45ca-8342-67796e11b730
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 74c5beec4459c1d261a1850b9888a6a0906e9900
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="dimension-mdx"></a>Dimension (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="see-also"></a>См. также:  
 [Число &#40; Уровни иерархии &#41; &#40; Многомерные Выражения &#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Число &#40; Выбрать &#41; &#40; Многомерные Выражения &#41;](../mdx/count-set-mdx.md)   
 [Уровни &#40; Многомерные Выражения &#41;](../mdx/levels-mdx.md)   
 [Члены &#40; Выбрать &#41; &#40; Многомерные Выражения &#41;](../mdx/members-set-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
