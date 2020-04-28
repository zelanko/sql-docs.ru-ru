---
title: BottomSum (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2e49fc5a7ffd4c0adff38628a143ded695785e29
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68016886"
---
# <a name="bottomsum-mdx"></a>BottomSum (многомерные выражения)


  Сортирует заданный набор по возрастанию и возвращает набор кортежей с наименьшими значениями, совокупное значение которых меньше или равно заданному значению.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BottomSum(Set_Expression, Value, Numeric_Expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Значение*  
 Допустимое числовое выражение, указывающее величину, с которой сравнивается каждый кортеж.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Remarks  
 Функция **BottomSum** вычисляет сумму указанной меры, вычисленную на указанном множестве, отсортированную по возрастанию. Функция возвращает элементы с самыми низкими значениями, чьи итоги на основе указанного числового выражения по меньшей мере равны заданному значению. Функция возвращает самый маленький поднабор набора, совокупное значение которого равно по меньшей мере заданному значению. Возвращенные элементы упорядочены по возрастанию.  
  
> [!IMPORTANT]  
>  Функция **BottomSum** , как и функция [TopSum](../mdx/topsum-mdx.md) , всегда прерывает иерархию.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается наименьший набор элементов уровня City в иерархии Geography в измерении Geography за 2003 финансовый год для категории Bike, чей совокупный итог по мере Reseller Sales Amount составляет не менее 50 000.  
  
 `SELECT`  
  
 `[Product].[Product Categories].Bikes ON 0,`  
  
 `BottomSum`  
  
 `({[Geography].[Geography].[City].Members}`  
  
 `, 50000`  
  
 `, ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)`  
  
 `) ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
