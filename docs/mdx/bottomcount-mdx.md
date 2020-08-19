---
description: BottomCount (многомерные выражения)
title: BottomCount (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e331a84efe36cef11951afac3f304957e4ffcb00
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494983"
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
  
## <a name="remarks"></a>Remarks  
 Если числовое выражение указано, эта функция сортирует кортежи заданного набора по значениям числового выражения, вычисленного над набором, в порядке возрастания. Затем функция **BottomCount** возвращает указанное число кортежей с наименьшим значением.  
  
> [!IMPORTANT]  
>  Функция **BottomCount** , как и функция [TopCount](../mdx/topcount-mdx.md) , всегда прерывает иерархию.  
  
 Если числовое выражение не указано, функция возвращает набор элементов в естественном порядке без какой-либо сортировки, как в функции [tail (многомерные выражения)](../mdx/tail-mdx.md) .  
  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
