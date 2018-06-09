---
title: WTD (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9a548f25d9114e9032f2462bbc97bda637abd6d9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743784"
---
# <a name="wtd-mdx"></a>Wtd (многомерные выражения)


  Возвращает набор элементов с общим родителем, находящихся на том же уровне, что и данный элемент, начиная с первого такого элемента и заканчивая данным элементом, в соответствии с ограничениями уровня Week в измерении Time.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Wtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 Если выражение элемента не указано, по умолчанию используется текущий элемент первой иерархии с уровнем типа недель в первом измерении типа Time (**Time.CurrentMember**) в группе мер.  
  
 **Wtd** функция — это функция ярлык для [PeriodsToDate](../mdx/periodstodate-mdx.md) функции, где устанавливается уровень *недели*. Таким образом, вызов `Wtd(Member_Expression)` эквивалентен вызову `PeriodsToDate(Week_Level_Expression,Member_Expression)`.  
  
## <a name="see-also"></a>См. также  
 [QTD &#40;многомерных Выражений&#41;](../mdx/qtd-mdx.md)   
 [MTd &#40;многомерных Выражений&#41;](../mdx/mtd-mdx.md)   
 [С начала года &#40;многомерных Выражений&#41;](../mdx/ytd-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
