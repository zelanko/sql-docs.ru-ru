---
title: Value (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 299004e869aeab826e5f1207a0ecc4d31639e2c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037938"
---
# <a name="value-mdx"></a>Value (многомерные выражения)


  Возвращает значение текущего элемента измерения «Measures», пересекающееся с текущим элементом иерархий атрибута в контексте запроса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression[.Value]   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 **Значение** функция возвращает значение указанного элемента в виде строки. **Значение** аргумент является необязательным, так как значение элемента — стандартное свойство элемента и значение, возвращаемое для элемента в том случае, если другое значение не указано. Дополнительные сведения о свойствах элементов см. в разделе [внутренние свойства элементов &#40;многомерных Выражений&#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md) и [пользовательские свойства элементов &#40;многомерных Выражений&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [MemberValue &#40;многомерных Выражений&#41;](../mdx/membervalue-mdx.md)   
 [Properties (многомерные выражения)](../mdx/properties-mdx.md)   
 [Имя &#40;многомерных Выражений&#41;](../mdx/name-mdx.md)   
 [UniqueName &#40;многомерных Выражений&#41;](../mdx/uniquename-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
