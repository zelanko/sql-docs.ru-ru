---
title: Value (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f373f626d778c4d77ec5843dca5bb11da728451d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68887445"
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
  
## <a name="remarks"></a>Remarks  
 Функция **value** возвращает значение указанного элемента в виде строки. Аргумент **value** является необязательным, так как значение элемента является свойством по умолчанию элемента и является значением, возвращаемым для элемента, если другое значение не указано. Дополнительные сведения о свойствах элементов см. в разделе [внутренние свойства элементов &#40;&#41;многомерных выражений](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties) и [определяемые пользователем свойства элементов &#40;&#41;многомерных выражений ](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties).  
  
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
 [MemberValue &#40;&#41;многомерных выражений](../mdx/membervalue-mdx.md)   
 [Свойства &#40;&#41;многомерных выражений](../mdx/properties-mdx.md)   
 [Имя &#40;&#41;многомерных выражений](../mdx/name-mdx.md)   
 [Уникальное &#40;&#41;многомерных выражений](../mdx/uniquename-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
