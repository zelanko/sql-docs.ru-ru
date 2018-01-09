---
title: "Count (кортеж) (многомерные Выражения) | Документы Microsoft"
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
f1_keywords: COUNT
dev_langs: kbMDX
helpviewer_keywords: Count function [MDX]
ms.assetid: c8f4a570-54a8-4c00-ac4b-eef0ebdb353c
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 76bea834dccee153edf96c78175f290a4e5551c5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="count-tuple-mdx"></a>Count (кортеж) (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает количество измерений в кортеже.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Tuple_Expression.Count  
```  
  
## <a name="arguments"></a>Аргументы  
 *Tuple_Expression*  
 Допустимое многомерное выражение, возвращающее кортеж.  
  
## <a name="remarks"></a>Remarks  
 Возвращает количество измерений в кортеже.  
  
## <a name="example"></a>Пример  
 Вычисленная мера в приведенном ниже запросе возвращает значение 2, которое представляет число иерархий в кортеже `([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001])`.  
  
```  
WITH MEMBER MEASURES.COUNTTUPLE AS  
COUNT(([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001]))  
SELECT MEASURES.COUNTTUPLE ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Число &#40; измерения &#41; &#40; Многомерные Выражения &#41;](../mdx/count-dimension-mdx.md)   
 [Число &#40; Уровни иерархии &#41; &#40; Многомерные Выражения &#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Число &#40; Выбрать &#41; &#40; Многомерные Выражения &#41;](../mdx/count-set-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
