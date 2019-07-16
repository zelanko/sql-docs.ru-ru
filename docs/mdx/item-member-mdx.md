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
ms.openlocfilehash: d7afa88f9d6239c8da7cb9c406ef11f0764f8dcf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905913"
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
  
  
