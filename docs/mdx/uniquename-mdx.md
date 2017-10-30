---
title: "UniqueName (многомерные Выражения) | Документы Microsoft"
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
- UNIQUENAME
dev_langs:
- kbMDX
helpviewer_keywords:
- UniqueName function
ms.assetid: f186094e-670c-401c-a82f-6b634b3f71f5
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ba317c8f76dceec65aa7229c7837311671a4658c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="uniquename-mdx"></a>UniqueName (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает уникальное имя указанного измерения, иерархии, уровня или элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Dimension expression syntax  
Dimension_Expression.UniqueName  
  
Hierarchy expression syntax  
Hierarchy_Expression.UniqueName  
  
Level expression syntax  
Level_Expression.UniqueName  
  
Member expression syntax  
Member_Expression.UniqueName  
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
  
## <a name="remarks"></a>Замечания  
 **UniqueName** функция возвращает уникальное имя объекта, а не имя, возвращаемое функцией [имя](../mdx/name-mdx.md) функции. Возвращаемое имя не включает имя куба. Возвращаемые результаты зависят от параметров сервера или от свойства многомерных выражений, задающего уникальную строку подключения.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается уникальное имя для измерения «Product», иерархии «Product Categories», уровня «Subcategory» и элемента «Bike Racks» в кубе «Adventure Works».  
  
```  
WITH MEMBER DimensionUniqueName   
   AS [Product].UniqueName  
MEMBER HierarchyUniqueName   
   AS [Product].[Product Categories].UniqueName  
MEMBER LevelUniqueName   
   AS [Product].[Product Categories].[Subcategory].UniqueName  
MEMBER MemberUniqueName   
   AS [Product].[Product Categories].[Subcategory].[Bike Racks]  
SELECT   
   {DimensionUniqueName  
   , HierarchyUniqueName  
   , LevelUniqueName  
   , MemberUniqueName }  
   ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

