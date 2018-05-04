---
title: Count (измерение) (многомерные Выражения) | Документы Microsoft
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
- COUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- Count function [MDX]
ms.assetid: 4b9c52f6-5bb0-401a-947c-e14134558b4a
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: ac6f91e0b54e5c50acde00c6cd59eaee2131b23d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="count-dimension-mdx"></a>Count (измерение) (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает количество иерархий куба.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Dimensions.Count   
```  
  
## <a name="remarks"></a>Замечания  
 Возвращает количество иерархий куба, включая иерархию `[Measures].[Measures]`.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается количество иерархий в кубе Adventure Works.  
  
```  
WITH MEMBER measures.X AS  
  dimensions.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Число &#40;кортежа&#41; &#40;многомерных Выражений&#41;](../mdx/count-tuple-mdx.md)   
 [Число &#40;уровней иерархии&#41; &#40;многомерных Выражений&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Число & #40; Выбрать & #41; & #40; Многомерные Выражения & #41;](../mdx/count-set-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
