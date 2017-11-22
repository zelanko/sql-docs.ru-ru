---
title: "Item (элемент) (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ITEM
dev_langs: kbMDX
helpviewer_keywords: Item function
ms.assetid: 71cca249-910b-4ecd-9097-1a17b224e219
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6f35b9e90c01f55e66045ae54d6f8c3b8e2166e0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="item-member-mdx"></a>Item (элемент) (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>Замечания  
 **Элемент** функция возвращает элемент указанного кортежа. Функция возвращает элемент, находящийся в позиции (с нуля), заданной параметром *индекса*.  
  
## <a name="example"></a>Пример  
 Следующий пример возвращает элемент `[2003]` — первый элемент в кортеже `[Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).` — в столбцах:  
  
 `SELECT`  
  
 `{( [Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).Item(0)} ON 0`  
  
 `,{[Measures].[Reseller Sales Amount]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
