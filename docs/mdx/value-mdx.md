---
title: "Значение (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Value
dev_langs: kbMDX
helpviewer_keywords: Value function
ms.assetid: ff76628e-2d49-49f6-a6cb-f6da07d83d65
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ac0f17b4afd4205c2173ff756c736e44d8d0d3d7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="value-mdx"></a>Value (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает значение текущего элемента измерения «Measures», пересекающееся с текущим элементом иерархий атрибута в контексте запроса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression[.Value]   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Замечания  
 **Значение** функция возвращает значение указанного элемента в виде строки. **Значение** аргумент является необязательным, так как значение элемента — стандартное свойство элемента, а значение, возвращаемое для элемента, если никакое другое значение не указано. Дополнительные сведения о свойствах элементов см. в разделе [внутренние свойства элементов &#40; Многомерные Выражения &#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md) и [определенных пользователем свойств элементов &#40; Многомерные Выражения &#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере явно возвращается имя элемента и его значение.  
  
```  
WITH MEMBER [Date].[Calendar].NumericValue as [Date].[Calendar].[July 1, 2001].Value  
MEMBER [Date].[Calendar].MemberName AS [Date].[Calendar].[July 1, 2001].Name  
  
SELECT {[Date].[Calendar].NumericValue, [Date].[Calendar].MemberName} ON 0  
from [Adventure Works]  
```  
  
 В следующем примере возвращается значение элемента как стандартное, возвращаемое для элемента по оси.  
  
```  
SELECT {[Date].[Calendar].[July 1, 2001]} ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [MemberValue &#40; Многомерные Выражения &#41;](../mdx/membervalue-mdx.md)   
 [Свойства &#40; Многомерные Выражения &#41;](../mdx/properties-mdx.md)   
 [Имя &#40; Многомерные Выражения &#41;](../mdx/name-mdx.md)   
 [UniqueName &#40; Многомерные Выражения &#41;](../mdx/uniquename-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
