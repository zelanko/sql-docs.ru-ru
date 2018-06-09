---
title: HEAD (MDX) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 05cfcb3c23a0369f010b8440d4a27e94ffacdb21
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740483"
---
# <a name="head-mdx"></a>Head (многомерные выражения)


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
  
## <a name="remarks"></a>Примечания  
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
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
