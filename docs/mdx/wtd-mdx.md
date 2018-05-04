---
title: WTD (многомерные Выражения) | Документы Microsoft
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
- WTD
dev_langs:
- kbMDX
helpviewer_keywords:
- Wtd function
ms.assetid: 41066e1b-e802-4582-be4b-3ed7807b033e
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 83fc733e36f6e68674d3f32b47087090499cf7cd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="wtd-mdx"></a>Wtd (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор элементов с общим родителем, находящихся на том же уровне, что и данный элемент, начиная с первого такого элемента и заканчивая данным элементом, в соответствии с ограничениями уровня Week в измерении Time.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Wtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Замечания  
 Если выражение элемента не указано, по умолчанию используется текущий элемент первой иерархии с уровнем типа недель в первом измерении типа Time (**Time.CurrentMember**) в группе мер.  
  
 **Wtd** функция — это функция ярлык для [PeriodsToDate](../mdx/periodstodate-mdx.md) функции, где устанавливается уровень *недели*. Таким образом, вызов `Wtd(Member_Expression)` эквивалентен вызову `PeriodsToDate(Week_Level_Expression,Member_Expression)`.  
  
## <a name="see-also"></a>См. также  
 [QTD &#40;многомерных Выражений&#41;](../mdx/qtd-mdx.md)   
 [MTd &#40;многомерных Выражений&#41;](../mdx/mtd-mdx.md)   
 [С начала года &#40;многомерных Выражений&#41;](../mdx/ytd-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
