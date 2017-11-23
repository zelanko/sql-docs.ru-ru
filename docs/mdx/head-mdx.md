---
title: "HEAD (MDX) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: HEAD
dev_langs: kbMDX
helpviewer_keywords: Head function
ms.assetid: 2a909bda-1366-4537-93b0-c089554fc11f
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: fa23c17ba90453c735c41782c208f388d706f434
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="head-mdx"></a>Head (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает указанное количество первых элементов набора, сохраняя повторяющиеся элементы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Head(Set_Expression [ ,Count ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Счетчик*  
 Допустимое числовое выражение, указывающее количество возвращаемых кортежей.  
  
## <a name="remarks"></a>Замечания  
 **Head** функция возвращает заданное количество кортежей из начала указанного набора. Порядок элементов сохраняется. Значение Count по умолчанию равно 1. Если заданное количество кортежей меньше 1, **Head** функция возвращает пустой набор. Если заданное число кортежей превышает количество кортежей в наборе, то функция возвращает исходный набор.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается пять подкатегорий наиболее продаваемых товаров вне зависимости от иерархии, основываясь на значении меры Reseller Gross Profit. **Head** функция используется для возвращения только первые пять наборов в результате после упорядочивания результата с помощью **порядок** функции.  
  
```  
SELECT   
[Measures].[Reseller Gross Profit] ON 0,  
Head  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BDESC  
      )  
   ,5  
   ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Резервная копия заключительного &#40; Многомерные Выражения &#41;](../mdx/tail-mdx.md)   
 [Элемент &#40; Кортеж &#41; &#40; Многомерные Выражения &#41;](../mdx/item-tuple-mdx.md)   
 [Элемент &#40; Элемент &#41; &#40; Многомерные Выражения &#41;](../mdx/item-member-mdx.md)   
 [Ранг &#40; Многомерные Выражения &#41;](../mdx/rank-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
