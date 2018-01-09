---
title: "WTD (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: WTD
dev_langs: kbMDX
helpviewer_keywords: Wtd function
ms.assetid: 41066e1b-e802-4582-be4b-3ed7807b033e
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: dd738d665a8dd94758d665828174b244622a3190
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
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
  
## <a name="remarks"></a>Remarks  
 Если выражение элемента не указано, по умолчанию используется текущий элемент первой иерархии с уровнем типа недель в первом измерении типа Time (**Time.CurrentMember**) в группе мер.  
  
 **Wtd** функция — это функция ярлык для [PeriodsToDate](../mdx/periodstodate-mdx.md) функции, где устанавливается уровень *недели*. Таким образом, вызов `Wtd(Member_Expression)` эквивалентен вызову `PeriodsToDate(Week_Level_Expression,Member_Expression)`.  
  
## <a name="see-also"></a>См. также:  
 [QTD &#40; Многомерные Выражения &#41;](../mdx/qtd-mdx.md)   
 [MTd &#40; Многомерные Выражения &#41;](../mdx/mtd-mdx.md)   
 [YTD &#40; Многомерные Выражения &#41;](../mdx/ytd-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
