---
title: "Count (уровни иерархии) (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- Count function [MDX]
ms.assetid: 3de6a824-2ff3-47ac-9ceb-e3369a04f35d
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d3e031210ea5b19628bc11a044b5c3977c465b9a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="count-hierarchy-levels-mdx"></a>Count (уровни иерархии) (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает количество уровней в иерархии.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchy_Expression.Levels.Count  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
## <a name="remarks"></a>Замечания  
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
  
## <a name="see-also"></a>См. также:  
 [Число &#40; измерения &#41; &#40; Многомерные Выражения &#41;](../mdx/count-dimension-mdx.md)   
 [Число &#40; Кортеж &#41; &#40; Многомерные Выражения &#41;](../mdx/count-tuple-mdx.md)   
 [Число &#40; Выбрать &#41; &#40; Многомерные Выражения &#41;](../mdx/count-set-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

