---
title: SetToArray (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SETTOARRAY
dev_langs:
- kbMDX
helpviewer_keywords:
- SetToArray function
ms.assetid: e408c626-3a2a-4ce9-aeb4-247301334893
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 930a3098edd4540222ddade44423724b85956137
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="settoarray-mdx"></a>SetToArray (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Замечания  
 **SetToArray** функция преобразует один или несколько наборов в массив для использования в определяемой пользователем функции. Число измерений результирующего массива равно числу заданных наборов.  
  
 Необязательное числовое выражение может задавать значения в ячейках массива. Если числовое выражение не указано, то перекрестное соединение наборов определяется в текущем контексте.  
  
 Координаты ячеек результирующего массива соответствуют позиции наборов в списке. Пусть существует три набора: `SA`, `SB` и `SC`. Каждый из этих наборов имеет два элемента. Инструкция многомерных выражений `SetToArray(SA, SB, SC)` создает следующий трехмерный массив:  
  
```  
(SA1, SB1, SC1) (SA2, SB1, SC1) (SA1, SB2, SC1) (SA2, SB2, SC1)   
(SA1, SB1, SC2) (SA2, SB1, SC2) (SA1, SB2, SC2) (SA2, SB2, SC2)   
```  
  
> [!NOTE]  
>  Тип возвращаемого значения **SetToArray** функция имеет тип VARIANT, то есть VT_ARRAY. Таким образом, выходные данные **SetToArray** функцию следует использовать только в качестве входных данных для определяемой пользователем функции.  
  
## <a name="example"></a>Пример  
 Следующий пример возвращает массив.  
  
```  
SetToArray([Geography].[Geography].Members, [Measures].[Internet Sales Amount])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
