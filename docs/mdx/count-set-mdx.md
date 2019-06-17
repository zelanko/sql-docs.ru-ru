---
title: Count (набор) (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 31e048329fde26d947b7d7978ee2d364d4901b34
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63285003"
---
# <a name="count-set-mdx"></a>Count (набор) (многомерные выражения)


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
  
## <a name="remarks"></a>Примечания  
 **Count (набор)** функция включает или исключает пустые ячейки, в зависимости от синтаксиса, используемого. Если используется стандартный синтаксис, пустые ячейки можно для включения или исключения с помощью **EXCLUDEEMPTY** или **INCLUDEEMPTY** флаги, соответственно. Если используется альтернативный синтаксис, то функция всегда включает пустые ячейки.  
  
 Чтобы исключить пустые ячейки при подсчете элементов множества, используйте стандартный синтаксис и необязательный **EXCLUDEEMPTY** флаг.  
  
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
  
 В следующем примере подсчитывается количество продуктов в измерении Product с помощью **DrilldownLevel** функция в сочетании с **число** функции.  
  
```  
Count(DrilldownLevel (   
   [Product].[Product].[Product]))  
```  
  
 В следующем примере возвращаются посредники, продажи по сравнению с предыдущим календарным кварталом, с помощью которых снизились **число** функция в сочетании с **фильтра** и ряда других функции. В этом запросе **агрегатные** функции для поддержки выбора нескольких элементов географии, например, для выбора из в раскрывающемся списке в клиентском приложении.  
  
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
  
## <a name="see-also"></a>См. также  
 [Число &#40;измерения&#41; &#40;многомерных Выражений&#41;](../mdx/count-dimension-mdx.md)   
 [Число &#40;уровней иерархии&#41; &#40;многомерных Выражений&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Число &#40;кортежа&#41; &#40;многомерных Выражений&#41;](../mdx/count-tuple-mdx.md)   
 [DrilldownLevel (многомерные выражения)](../mdx/drilldownlevel-mdx.md)   
 [AddCalculatedMembers (многомерные выражения)](../mdx/addcalculatedmembers-mdx.md)   
 [Hierarchize (многомерные выражения)](../mdx/hierarchize-mdx.md)   
 [Properties (многомерные выражения)](../mdx/properties-mdx.md)   
 [Aggregate (многомерные выражения)](../mdx/aggregate-mdx.md)   
 [Filter (многомерные выражения)](../mdx/filter-mdx.md)   
 [PrevMember (многомерные выражения)](../mdx/prevmember-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
