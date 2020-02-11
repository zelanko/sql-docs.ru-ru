---
title: Count (набор) (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: aac2f72cc8cd91e1964fd7734b858be8215cfdd8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68047292"
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
  
## <a name="remarks"></a>Remarks  
 Функция **Count (Set)** включает или исключает пустые ячейки в зависимости от используемого синтаксиса. Если используется стандартный синтаксис, пустые ячейки могут быть исключены или включены с помощью флагов **ексклудимпти** или **INCLUDEEMPTY** соответственно. Если используется альтернативный синтаксис, то функция всегда включает пустые ячейки.  
  
 Чтобы исключить пустые ячейки в количестве набора, используйте стандартный синтаксис и необязательный флаг **ексклудимпти** .  
  
> [!NOTE]  
>  Функция **Count (Set)** Подсчитывает пустые ячейки по умолчанию. В отличие от этого функция **Count** в OLE DB, которая подсчитывает набор, исключает пустые ячейки по умолчанию.  
  
## <a name="examples"></a>Примеры  
 В следующем примере подсчитывается количество ячеек в наборе элементов, состоящем из потомков иерархии атрибута Model Name в измерении Product.  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Model Name].children.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере подсчитывается количество продуктов в измерении Product с помощью функции **DrilldownLevel** в сочетании с функцией **Count** .  
  
```  
Count(DrilldownLevel (   
   [Product].[Product].[Product]))  
```  
  
 В следующем примере возвращаются торговые посредники с отклонением продаж по сравнению с предыдущим календарным кварталом с помощью функции **Count** в сочетании с функцией **Filter** и несколькими другими функциями. Этот запрос использует **агрегатную** функцию для поддержки выбора нескольких географических элементов, например для выбора из раскрывающегося списка в клиентском приложении.  
  
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
 [Счетчик &#40;измерение&#41; &#40;&#41;многомерных выражений](../mdx/count-dimension-mdx.md)   
 [Количество &#40;уровней иерархии&#41; &#40;МНОГОМЕРных&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Счетчик &#40;кортеж&#41; &#40;многомерных выражений&#41;](../mdx/count-tuple-mdx.md)   
 [DrilldownLevel &#40;&#41;многомерных выражений](../mdx/drilldownlevel-mdx.md)   
 [AddCalculatedMembers &#40;&#41;многомерных выражений](../mdx/addcalculatedmembers-mdx.md)   
 [Hierarchize &#40;&#41;многомерных выражений](../mdx/hierarchize-mdx.md)   
 [Свойства &#40;&#41;многомерных выражений](../mdx/properties-mdx.md)   
 [Статистическая обработка &#40;многомерных выражений&#41;](../mdx/aggregate-mdx.md)   
 [Фильтрация &#40;&#41;многомерных выражений](../mdx/filter-mdx.md)   
 [PrevMember &#40;&#41;многомерных выражений](../mdx/prevmember-mdx.md)   
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
