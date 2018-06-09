---
title: Min (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 85d48badaa1b50edec6a563decbead1a38f5fcb0
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741993"
---
# <a name="min-mdx"></a>Min (многомерные выражения)


  Возвращает минимальное значение числового выражения, вычисляемого на наборе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Min( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Примечания  
 Если числовое выражение указано, оно вычисляется для всех элементов набора и возвращается минимальное значение вычислений. Если числовое выражение не указано, указанный набор вычисляется в текущем контексте элементов набора и возвращается минимальное значение вычислений.  
  
> [!NOTE]  
>  Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] отбрасывает неопределенные значения при вычислении минимального значения набора чисел.   
  
## <a name="example"></a>Пример  
 В следующем примере возвращается минимум квартальных продаж для каждой подкатегории и каждой страны в кубе Adventure Works.  
  
```  
WITH MEMBER Measures.x AS Min   
   ([Date].[Calendar].CurrentMember.Children  
      , [Measures].[Reseller Order Quantity]  
   )  
SELECT Measures.x ON 0  
,NON EMPTY [Date].[Calendar].[Calendar Quarter]*   
   [Product].[Product Categories].[Subcategory].members *  
   [Geography].[Geography].[Country].Members  
ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
