---
title: MTd (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e38d8d3485e50054ee4d1106b1ef7bdfc8ce96ea
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580766"
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
  
## <a name="remarks"></a>Примечания  
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
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
