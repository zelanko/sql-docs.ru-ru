---
title: "Members (Set) (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Members
dev_langs: kbMDX
helpviewer_keywords: Members function
ms.assetid: 0c4d5bb9-500b-47ce-b7fc-f5a10e2400e0
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 89af65f48bc976c42a9a45c8a25c676cb16ac6f1
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="members-set-mdx"></a>Members (набор) (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор элементов в измерении, уровне или иерархии.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchy expression syntax  
Hierarchy_Expression.Members  
  
Level expression Syntax  
Level_Expression.Members  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
## <a name="remarks"></a>Замечания  
 Если указано выражение иерархии, **Members (Set)** функция возвращает набор всех элементов указанной иерархии, не включая вычисляемые элементы. Чтобы получить набор всех элементов, вычисляемых или в противном случае в иерархии, используйте [AllMembers &#40; Многомерные Выражения &#41; ](../mdx/allmembers-mdx.md) функции  
  
 Если выражение уровня указано, **Members (Set)** функция возвращает набор всех элементов указанного уровня.  
  
> [!IMPORTANT]  
>  Если измерение содержит единственную видимую иерархию, на нее можно сослаться по имени измерения или по имени иерархии, поскольку имя измерения в этом случае разрешается в единственную видимую иерархию. Например, многомерное выражение Measures.Members является допустимым, поскольку измерение Measures разрешается в единственную видимую иерархию.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все элементы иерархии Calendar Year в кубе Adventure Works.  
  
```  
SELECT   
   [Date].[Calendar].[Calendar Year].Members ON 0  
FROM  
   [Adventure Works]  
  
```  
  
 В следующем примере возвращается количество заказов за 2003 год для каждого элемента уровня `[Product].[Products].[Product Line]`. **Члены** функция возвращает набор, представляющий все элементы на том уровне.  
  
```  
SELECT   
   {Measures.[Order Quantity]} ON COLUMNS,  
   [Product].[Product Line].[Product Line].Members ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
