---
title: "Item (кортеж) (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ITEM
dev_langs: kbMDX
helpviewer_keywords: Item function
ms.assetid: 9ee7af55-d5b5-47c8-a480-ef23878306af
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 45b34c8625837db7c379aa981f834559c4a033b6
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="item-tuple-mdx"></a>Item (кортеж) (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает кортеж из набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Index syntax  
Set_Expression.Item(Index)  
  
String expression syntax  
Set_Expression.Item(String_Expression1 [ ,String_Expression2,...n])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Выражение String_Expression1*  
 Допустимое строковое выражение, обычно являющееся кортежем в форме строки.  
  
 *Выражение String_Expression2*  
 Допустимое строковое выражение, обычно являющееся кортежем в форме строки.  
  
 *Index*  
 Допустимое числовое выражение, указывающее кортеж по его позиции в возвращаемом наборе.  
  
## <a name="remarks"></a>Замечания  
 **Элемент** функция возвращает кортеж из указанного набора. Существует три способа вызвать **элемент** функции:  
  
-   Если одно строковое выражение указано, **элемент** функция возвращает заданный кортеж. Пример: "([2005].Q3, [Store05])".  
  
-   Если указано более одного строковое выражение, **элемент** функция возвращает кортеж, определяемый по заданным координатам. Количество строк должно совпадать с количеством осей, а каждая строка — обозначать уникальную иерархию. Пример: "[2005].Q3", "[Store05]".  
  
-   Если указано целое число, **элемент** функция возвращает кортеж, который находится в позиции (с нуля), заданной параметром *индекса*.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает ([1996],Sales):  
  
 `{([1996],Sales), ([1997],Sales), ([1998],Sales)}.Item(0)`  
  
 В следующем примере используется выражение уровня и возвращается Internet Sales Amount для каждой административно-территориальной единицы (State-Province) Австралии (Australia), возвращается также процентное соотношение относительно общего значения Internet Sales Amount в Австралии (Australia). В этом примере используется функция Item для извлечения из набора, возвращаемого первым (и только кортежа) **предков** функции.  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   ( [Measures].[Internet Sales Amount],    
      Ancestors   
      ( [Customer].[Customer Geography].CurrentMember,  
        [Customer].[Customer Geography].[Country]  
      ).Item (0)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{ Descendants   
   ( [Customer].[Customer Geography].[Country].&[Australia],  
     [Customer].[Customer Geography].[State-Province], SELF   
   )   
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
