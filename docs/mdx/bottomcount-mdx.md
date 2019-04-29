---
title: BottomCount (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 424c928f64b784070520f4cebe450dd5465fea41
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181630"
---
# <a name="bottomcount-mdx"></a>BottomCount (многомерные выражения)


  Сортирует набор в порядке возрастания и возвращает указанное число кортежей набора с минимальными значениями.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BottomCount(Set_Expression, Count [,Numeric_Expression])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Count*  
 Допустимое числовое выражение, указывающее количество возвращаемых кортежей.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Примечания  
 Если числовое выражение указано, эта функция сортирует кортежи заданного набора по значениям числового выражения, вычисленного над набором, в порядке возрастания. **BottomCount** функция затем возвращает заданное число кортежей с наименьшими значениями.  
  
> [!IMPORTANT]  
>  **BottomCount** функция, как и [TopCount](../mdx/topcount-mdx.md) функции, всегда нарушает иерархию.  
  
 Если числовое выражение не указано, функция возвращает набор элементов в естественном порядке без какой-либо сортировки, ведет себя подобно [Tail (MDX)](../mdx/tail-mdx.md) функции.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается мера Reseller Order Quantity для пяти элементов Product SubCategory с наименьшими значениями в каждом календарном году, отсортированных по мере Reseller Sales Amount.  
  
```  
SELECT BottomCount([Product].[Product Categories].[Subcategory].Members  
   , 10  
   , [Measures].[Reseller Sales Amount]) ON 0,  
   [Date].[Calendar].[Calendar Year].Members ON 1  
  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Reseller Order Quantity]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
