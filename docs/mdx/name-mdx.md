---
title: Name (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Name
dev_langs:
- kbMDX
helpviewer_keywords:
- Name function
ms.assetid: adb94151-2022-4167-92b2-d3125573144a
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6cf502fc684214011f903afb0761c98d86e2a80e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="name-mdx"></a>Name (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает имя измерения, иерархии, уровня или элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Dimension expression syntax  
Dimension_Expression.Name  
  
Hierarchy expression syntax  
Hierarchy_Expression.Name  
  
Level_expression syntax  
Level_Expression.Name  
  
Member expression syntax  
Member_Expression.Name  
```  
  
## <a name="arguments"></a>Аргументы  
 *Аргумент Dimension_Expression*  
 Допустимое многомерное выражение, возвращающее измерение.  
  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Remarks  
 **Имя** функция возвращает имя объекта, а не его уникальное имя.  
  
## <a name="examples"></a>Примеры  
  
### <a name="dimension-hierarchy-and-level-expression-example"></a>Выражения измерения, иерархии и уровня  
 В следующем примере возвращается имя измерения времени и иерархия и имена уровней для элемента July 2001.  
  
```  
WITH MEMBER Measures.DimensionName AS [Date].Name  
MEMBER Measures.HierarchyName AS [Date].[Calendar].[July 2001].Hierarchy.Name  
MEMBER Measures.LevelName as [Date].[Calendar].[July 2001].Level.Name  
  
SELECT {Measures.DimensionName, Measures.HierarchyName, Measures.LevelName} ON 0  
from [Adventure Works]  
```  
  
### <a name="member-expression-example"></a>Выражение элемента  
 В следующем примере возвращается имя элемента вместе с его значением, ключом и заголовком.  
  
```  
WITH MEMBER MemberName AS [Date].[Calendar].[July 1, 2001].Name  
MEMBER Measures.ValueColumn as [Date].[Calendar].[July 1, 2001].MemberValue  
MEMBER Measures.KeyColumn as [Date].[Calendar].[July 1, 2001].Member_Key  
MEMBER Measures.NameColumn as [Date].[Calendar].[July 1, 2001].Member_Name  
  
SELECT {Measures.MemberName, Measures.ValueColumn, Measures.KeyColumn, Measures.NameColumn} ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
