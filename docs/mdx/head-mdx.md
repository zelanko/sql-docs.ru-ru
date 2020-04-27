---
title: Head (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6e6d8da7a5813f7e99c022e19f18de2800598885
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67906006"
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
  
 *Count*  
 Допустимое числовое выражение, указывающее количество возвращаемых кортежей.  
  
## <a name="remarks"></a>Remarks  
 Функция **head** возвращает указанное число кортежей из начала указанного набора. Порядок элементов сохраняется. Значение Count по умолчанию равно 1. Если указанное число кортежей меньше 1, функция **head** возвращает пустой набор. Если заданное число кортежей превышает количество кортежей в наборе, то функция возвращает исходный набор.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается пять подкатегорий наиболее продаваемых товаров вне зависимости от иерархии, основываясь на значении меры Reseller Gross Profit. Функция **head** используется для возвращения только первых пяти наборов в результате, когда результат упорядочивается с помощью функции **Order** .  
  
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
 [&#41;&#40;с хвостовиком хвоста](../mdx/tail-mdx.md)   
 [Элемент &#40;кортежа&#41; &#40;многомерных выражений&#41;](../mdx/item-tuple-mdx.md)   
 [Элемент &#40;элемента&#41; &#40;многомерных выражений&#41;](../mdx/item-member-mdx.md)   
 [Ранжирование &#40;&#41;многомерных выражений](../mdx/rank-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
