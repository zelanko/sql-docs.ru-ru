---
title: HEAD (многомерные Выражения) | Документация Майкрософт
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63125570"
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
  
## <a name="remarks"></a>Примечания  
 **Head** функция возвращает заданное количество кортежей из начала указанного набора. Порядок элементов сохраняется. Значение Count по умолчанию равно 1. Если заданное количество кортежей меньше 1, **Head** функция возвращает пустой набор. Если заданное число кортежей превышает количество кортежей в наборе, то функция возвращает исходный набор.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается пять подкатегорий наиболее продаваемых товаров вне зависимости от иерархии, основываясь на значении меры Reseller Gross Profit. **Head** функция используется для возврата только первые пять наборов в результате после упорядочивания результата с помощью **порядок** функции.  
  
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
 [Заключительный фрагмент &#40;многомерных Выражений&#41;](../mdx/tail-mdx.md)   
 [Элемент &#40;кортежа&#41; &#40;многомерных Выражений&#41;](../mdx/item-tuple-mdx.md)   
 [Элемент &#40;член&#41; &#40;многомерных Выражений&#41;](../mdx/item-member-mdx.md)   
 [Ранг &#40;многомерных Выражений&#41;](../mdx/rank-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
