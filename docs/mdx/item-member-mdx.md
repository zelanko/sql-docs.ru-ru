---
description: Item (элемент) (многомерные выражения)
title: Item (элемент) (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a374d1fcc7f972828832c2f82375acf640d45fb2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483967"
---
# <a name="item-member-mdx"></a>Item (элемент) (многомерные выражения)


  Возвращает элемент указанного кортежа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Tuple_Expression.Item( Index )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Tuple_Expression*  
 Допустимое многомерное выражение, возвращающее кортеж.  
  
 *Index*  
 Допустимое числовое выражение, указывающее положение элемента внутри возвращаемого кортежа.  
  
## <a name="remarks"></a>Remarks  
 Функция **Item** Возвращает элемент указанного кортежа. Функция возвращает элемент, найденный в позиции, начинающейся с нуля, указанной параметром *index*.  
  
## <a name="example"></a>Пример  
 Следующий пример возвращает элемент `[2003]` — первый элемент в кортеже `[Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).` — в столбцах:  
  
 `SELECT`  
  
 `{( [Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).Item(0)} ON 0`  
  
 `,{[Measures].[Reseller Sales Amount]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
