---
title: Count (набор) (многомерные Выражения) | Документы Microsoft
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
- COUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- Count function [MDX]
ms.assetid: 22f530e9-f8e1-4608-affa-9a2bc0821591
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 41d5ff72346e95985b19812f194d266e8d5db165
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="count-set-mdx"></a>Count (набор) (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает количество ячеек в наборе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Standard syntax  
Count(Set_Expression [ , ( EXCLUDEEMPTY | INCLUDEEMPTY ) ] )  
  
Alternate syntax  
Set_Expression.Count  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Remarks  
 **Count (набор)** функции включает или исключает пустые ячейки в зависимости от синтаксиса, который применяется. Если используется стандартный синтаксис, пустые ячейки могут для включения или исключения с помощью **EXCLUDEEMPTY** или **INCLUDEEMPTY** флаги, соответственно. Если используется альтернативный синтаксис, то функция всегда включает пустые ячейки.  
  
 Чтобы исключить пустые ячейки при подсчете элементов множества, используется стандартный синтаксис и необязательный **EXCLUDEEMPTY** флаг.  
  
> [!NOTE]  
>  **Count (набор)** функция подсчитывает пустые ячейки по умолчанию. Напротив **число** функции в OLE DB для подсчета элементов набора исключает пустые ячейки по умолчанию.  
  
## <a name="examples"></a>Примеры  
 В следующем примере подсчитывается количество ячеек в наборе элементов, состоящем из потомков иерархии атрибута Model Name в измерении Product.  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Model Name].children.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере подсчитывается количество продуктов в измерении Product с использованием **DrilldownLevel** функции вместе с **число** функции.  
  
```  
Count(DrilldownLevel (   
   [Product].[Product].[Product]))  
```  
  
 В следующем примере возвращаются посредники, продажи по сравнению с предыдущим календарным кварталом, с помощью которых снизились **число** функции вместе с **фильтра** функции и ряда других функций. В этом запросе используется **статистические** функции для поддержки выбора нескольких элементов географии, например для выбора из в раскрывающемся списке в клиентском приложении.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
   (Filter  
      (Existing(Reseller.Reseller.Reseller),  
         [Measures].[Reseller Sales Amount]   
         < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
      )  
   )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate  
   ( {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
   )  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})  
      })  
   ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,  
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
   ,[Measures].[Declining Reseller Sales])  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Число &#40; измерения &#41; &#40; Многомерные Выражения &#41;](../mdx/count-dimension-mdx.md)   
 [Число &#40; Уровни иерархии &#41; &#40; Многомерные Выражения &#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Число &#40; Кортеж &#41; &#40; Многомерные Выражения &#41;](../mdx/count-tuple-mdx.md)   
 [DrilldownLevel &#40; Многомерные Выражения &#41;](../mdx/drilldownlevel-mdx.md)   
 [AddCalculatedMembers &#40; Многомерные Выражения &#41;](../mdx/addcalculatedmembers-mdx.md)   
 [Hierarchize &#40; Многомерные Выражения &#41;](../mdx/hierarchize-mdx.md)   
 [Свойства &#40; Многомерные Выражения &#41;](../mdx/properties-mdx.md)   
 [Статистическая функция &#40; Многомерные Выражения &#41;](../mdx/aggregate-mdx.md)   
 [Фильтр &#40; Многомерные Выражения &#41;](../mdx/filter-mdx.md)   
 [PrevMember &#40; Многомерные Выражения &#41;](../mdx/prevmember-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
