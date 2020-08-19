---
description: Dimension (многомерные выражения)
title: Dimension (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9d4fff9d6ade52d4e8209e2a6e0cbecf99837d91
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484037"
---
# <a name="dimension-mdx"></a>Dimension (многомерные выражения)


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
  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
### <a name="examples"></a>Примеры  
 В следующем примере с помощью функции **Dimension** в сочетании с функцией **Name** возвращается имя иерархии указанного элемента.  
  
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
  
 В следующем примере используется функция **Dimension** в сочетании с функциями **Members** и **Count** , чтобы получить количество элементов в иерархии, содержащих указанный элемент.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Количество &#40;уровней иерархии&#41; &#40;МНОГОМЕРных&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Count &#40;Set&#41; &#40;многомерных выражений&#41;](../mdx/count-set-mdx.md)   
 [Уровни &#40;&#41;многомерных выражений ](../mdx/levels-mdx.md)   
 [Элементы &#40;задать&#41; &#40;многомерных выражений&#41;](../mdx/members-set-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
