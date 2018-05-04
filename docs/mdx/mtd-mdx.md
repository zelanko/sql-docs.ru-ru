---
title: MTd (многомерные Выражения) | Документы Microsoft
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
- MTD
dev_langs:
- kbMDX
helpviewer_keywords:
- Mtd function
ms.assetid: 07d8fd65-f9e6-42d4-868d-fccfac6bdb70
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b3c35a64883a8e7c7c3f09863f0ee36318654967
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mtd-mdx"></a>Mtd (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор элементов с общим родителем, находящихся на том же уровне, что и данный элемент, начиная с первого такого элемента и заканчивая данным элементом, в соответствии с ограничениями уровня Year в измерении Time.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Mtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Замечания  
 Если выражение элемента не указано, по умолчанию используется текущий элемент первой иерархии с уровнем типа *месяцев* в первом измерении типа *время* в группе мер.  
  
 **Mtd** функция — это функция ярлык для [PeriodsToDate](../mdx/periodstodate-mdx.md) функционировать, если значение свойства Type иерархии атрибута, на котором основан уровень *месяцев*. Таким образом, вызов `Mtd(Member_Expression)` эквивалентен вызову `PeriodsToDate(Month_Level_Expression,Member_Expression)`.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается сумма затрат на транспортировку товаров, заказанных через Интернет, за июль 2002 года, до 20 июля.  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Сумма &#40;многомерных Выражений&#41;](../mdx/sum-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
