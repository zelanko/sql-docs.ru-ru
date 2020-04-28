---
title: Median (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b6f941e269bb9948dd39ba52db0ea4d0961c029a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68033852"
---
# <a name="median-mdx"></a>Median (многомерные выражения)


  Возвращает медиант числового выражения, вычисляемого на наборе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Median(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Remarks  
 Если числовое выражение указано, оно вычисляется для всех элементов набора и затем возвращается медиана вычислений. Если числовое выражение не указано, указанный набор вычисляется в текущем контексте элементов набора и возвращается медиана вычислений.  
  
 Медиана — это значение из середины набора упорядоченных чисел. (Не путайте медиана со средним значением, которое представляет собой сумму набора чисел, разделенную на их количество). Для определения медианы находится такое наименьшее значение, которое не превышает минимум половину всех значений набора. Если набор содержит нечетное количество чисел, медиана равняется одному значению. Если количество чисел четное, медиана равняется усредненному значению двух чисел посередине.  
  
> [!NOTE]  
>  Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] не обрабатывают неопределенные значения при вычислении значения медианы для набора упорядоченных чисел.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается медиана сумм от продаж за месяц для каждого квартала и страны в кубе Adventure Works.  
  
```  
WITH MEMBER Measures.x AS Median   
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
