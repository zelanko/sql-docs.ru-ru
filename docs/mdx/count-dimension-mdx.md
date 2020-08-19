---
description: Count (измерение) (многомерные выражения)
title: Count (измерение) (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: afa58c330210e4fdb34d13892101e210f54cd3bd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429966"
---
# <a name="count-dimension-mdx"></a>Count (измерение) (многомерные выражения)


  Возвращает количество иерархий куба.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Dimensions.Count   
```  
  
## <a name="remarks"></a>Remarks  
 Возвращает количество иерархий куба, включая иерархию `[Measures].[Measures]`.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается количество иерархий в кубе Adventure Works.  
  
```  
WITH MEMBER measures.X AS  
  dimensions.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Счетчик &#40;кортеж&#41; &#40;многомерных выражений&#41;](../mdx/count-tuple-mdx.md)   
 [Количество &#40;уровней иерархии&#41; &#40;МНОГОМЕРных&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Count &#40;Set&#41; &#40;многомерных выражений&#41;](../mdx/count-set-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
