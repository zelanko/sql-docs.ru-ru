---
title: StdevP (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d4560ecbecd5db2e0f93e6910239fde27d54c028
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036876"
---
# <a name="stdevp-mdx"></a>StdevP (многомерные выражения)


  Возвращает среднеквадратичное отклонение совокупности числового выражения, вычисленное на наборе с использованием формулы смещенной совокупности (делением на *n*).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StdevP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Remarks  
 Функция **StDevP** использует формулу смещенной совокупности, а функция [STDEV](../mdx/stdev-mdx.md) использует формулу несмещенной совокупности.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается среднеквадратичное отклонение количества сделанных через Интернет заказов, которое вычисляется за первые три месяца 2003 г., при этом используется формула смещенной совокупности.  
  
```  
WITH MEMBER Measures.x AS   
   StdevP   
   ( { [Date].[Calendar].[Month].[January 2003],  
       [Date].[Calendar].[Month].[February 2003],  
       [Date].[Calendar].[Month].[March 2003]},  
    [Measures].[Internet Order Quantity])  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
