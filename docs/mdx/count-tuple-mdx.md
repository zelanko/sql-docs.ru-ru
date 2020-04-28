---
title: Count (кортеж) (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 486c68e1947bfad67bc0288751d03c6042cd7f3e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68047273"
---
# <a name="count-tuple-mdx"></a>Count (кортеж) (многомерные выражения)


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
 [Счетчик &#40;измерение&#41; &#40;&#41;многомерных выражений](../mdx/count-dimension-mdx.md)   
 [Количество &#40;уровней иерархии&#41; &#40;МНОГОМЕРных&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Count &#40;Set&#41; &#40;многомерных выражений&#41;](../mdx/count-set-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
