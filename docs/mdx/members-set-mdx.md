---
title: Members (Set) (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3bd4fe92c064f4665a4b397e47a45ae5bde50f39
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048455"
---
# <a name="members-set-mdx"></a>Members (набор) (многомерные выражения)


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
  
## <a name="remarks"></a>Примечания  
 Если выражение иерархии указано, **Members (Set)** функция возвращает набор всех элементов указанной иерархии, не включая вычисляемые элементы. Чтобы получить набор всех элементов, вычисляемых или в противном случае в иерархии, используйте [AllMembers &#40;многомерных Выражений&#41; ](../mdx/allmembers-mdx.md) функции  
  
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
  
 В следующем примере возвращается количество заказов за 2003 год для каждого элемента уровня `[Product].[Products].[Product Line]`. **Члены** функция возвращает набор, представляющий все элементы уровня.  
  
```  
SELECT   
   {Measures.[Order Quantity]} ON COLUMNS,  
   [Product].[Product Line].[Product Line].Members ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
