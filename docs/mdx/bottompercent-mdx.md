---
description: BottomPercent (многомерные выражения)
title: BottomPercent (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1b3ce341526270335564e9f67ccb89612854e098
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494986"
---
# <a name="bottompercent-mdx"></a>BottomPercent (многомерные выражения)


  Сортирует набор по возрастанию и возвращает набор кортежей с наименьшими значениями, совокупное значение которых больше или равно заданному проценту.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BottomPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Percentage*  
 Допустимое числовое выражение, указывающее процент возвращаемых кортежей.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Remarks  
 Функция **BottomPercent** вычисляет сумму указанного числового выражения, вычисленного на указанном наборе, отсортированного в возрастающем порядке. Затем функция возвращает элементы с наименьшими значениями, доля суммы которых в суммарном значении меньше или равна указанному проценту. Эта функция возвращает самый маленький поднабор набора, совокупное значение которого равно по меньшей мере заданному проценту. Возвращенные элементы упорядочены по убыванию.  
  
> [!IMPORTANT]  
>  Функция **BottomPercent** , как и функция [TopPercent](../mdx/toppercent-mdx.md) , всегда прерывает иерархию. Дополнительные сведения см. в описании функции Order.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается наименьший набор элементов уровня City в иерархии Geography в измерении Geography за 2003 финансовый год для категории Bike (начиная с элементов данного набора с наименьшим количеством продаж), совокупный итог этих элементов на основе меры Reseller Sales Amount равен по меньшей мере 15 %.  
  
```  
SELECT  
[Product].[Product Categories].Bikes ON 0,  
BottomPercent  
   ({[Geography].[Geography].[City].Members}  
   , 15  
   , ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)  
   ) ON 1  
FROM [Adventure Works]  
WHERE ([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
