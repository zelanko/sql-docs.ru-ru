---
title: Item (элемент) (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 92745085a408503a2b435eb160daf431c7fdaa32
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63272834"
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
  
## <a name="remarks"></a>Примечания  
 **Элемент** функция возвращает элемент указанного кортежа. Функция возвращает элемент, находящийся в позиции (с нуля), заданной параметром *индекс*.  
  
## <a name="example"></a>Пример  
 Следующий пример возвращает элемент `[2003]` — первый элемент в кортеже `[Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).` — в столбцах:  
  
 `SELECT`  
  
 `{( [Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).Item(0)} ON 0`  
  
 `,{[Measures].[Reseller Sales Amount]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
