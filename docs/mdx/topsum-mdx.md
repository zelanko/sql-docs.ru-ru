---
title: TopSum (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 853390f99f02352fd7814fcec208bba1508c03a7
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743413"
---
# <a name="topsum-mdx"></a>TopSum (многомерные выражения)


  Сортирует набор и возвращает самые верхние элементы, совокупное значение которых не меньше указанного значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TopSum(Set_Expression, Value, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Value*  
 Допустимое числовое выражение, указывающее величину, с которой сравнивается каждый кортеж.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение, которое обычно является многомерным выражением, возвращающим меру.  
  
## <a name="remarks"></a>Примечания  
 **TopSum** функция вычисляет сумму заданной меры, рассчитанной указанного набора, отсортированного в убывающем порядке. Функция возвращает элементы с самыми высокими значениями, чьи итоги на основе указанного числового выражения по меньшей мере равны заданному значению. Функция возвращает самый маленький поднабор набора, совокупное значение которого равно по меньшей мере заданному значению. Возвращенные элементы упорядочены по убыванию.  
  
> [!IMPORTANT]  
>  Как [BottomSum](../mdx/bottomsum-mdx.md) функции **TopSum** функция всегда нарушает иерархию.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается наименьший набор элементов уровня City в иерархии Geography в измерении Geography для категории Bike (начиная с элементов данного набора с наибольшим количеством продаж), совокупный итог этих элементов на основе меры Reseller Sales Amount равен по меньшей мере 6 000 000.  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopSum  
   ({[Geography].[Geography].[City].Members}  
   , 6000000  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
