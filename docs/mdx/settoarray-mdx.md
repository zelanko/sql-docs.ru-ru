---
title: SetToArray (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c52c2641d21c20c91ec7548cafc969e506801b08
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036991"
---
# <a name="settoarray-mdx"></a>SetToArray (многомерные выражения)


  Преобразует один или несколько наборов в массив для использования в пользовательской функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SetToArray(Set_Expression1 [ ,Set_Expression2,...n ][ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Примечания  
 **SetToArray** функция преобразует один или несколько наборов в массив для использования в определяемой пользователем функции. Число измерений результирующего массива равно числу заданных наборов.  
  
 Необязательное числовое выражение может задавать значения в ячейках массива. Если числовое выражение не указано, то перекрестное соединение наборов определяется в текущем контексте.  
  
 Координаты ячеек результирующего массива соответствуют позиции наборов в списке. Пусть существует три набора: `SA`, `SB` и `SC`. Каждый из этих наборов имеет два элемента. Инструкция многомерных выражений `SetToArray(SA, SB, SC)` создает следующий трехмерный массив:  
  
```  
(SA1, SB1, SC1) (SA2, SB1, SC1) (SA1, SB2, SC1) (SA2, SB2, SC1)   
(SA1, SB1, SC2) (SA2, SB1, SC2) (SA1, SB2, SC2) (SA2, SB2, SC2)   
```  
  
> [!NOTE]  
>  Тип возвращаемого значения **SetToArray** функция — это значения типа VARIANT, VT_ARRAY. Таким образом, выходные данные **SetToArray** функция должна использоваться только в качестве входных данных для определяемой пользователем функции.  
  
## <a name="example"></a>Пример  
 Следующий пример возвращает массив.  
  
```  
SetToArray([Geography].[Geography].Members, [Measures].[Internet Sales Amount])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
