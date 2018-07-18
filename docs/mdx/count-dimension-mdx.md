---
title: Count (измерение) (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6ee8fe09f7a840d32511d3a208a4621612ee9939
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740153"
---
# <a name="count-dimension-mdx"></a>Count (измерение) (многомерные выражения)


  Возвращает количество иерархий куба.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Dimensions.Count   
```  
  
## <a name="remarks"></a>Примечания  
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
 [Число &#40;задать&#41; &#40;многомерных Выражений&#41;](../mdx/count-set-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
