---
title: HEAD (MDX) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- HEAD
dev_langs:
- kbMDX
helpviewer_keywords:
- Head function
ms.assetid: 2a909bda-1366-4537-93b0-c089554fc11f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b0e25718c55dbe433bd34438b459aed31b2097f9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="head-mdx"></a>Head (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает указанное количество первых элементов набора, сохраняя повторяющиеся элементы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Head(Set_Expression [ ,Count ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Count*  
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
  
## <a name="see-also"></a>См. также  
 [Резервная копия заключительного &#40;многомерных Выражений&#41;](../mdx/tail-mdx.md)   
 [Элемент &#40;кортежа&#41; &#40;многомерных Выражений&#41;](../mdx/item-tuple-mdx.md)   
 [Элемент &#40;член&#41; &#40;многомерных Выражений&#41;](../mdx/item-member-mdx.md)   
 [Ранг &#40;многомерных Выражений&#41;](../mdx/rank-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
