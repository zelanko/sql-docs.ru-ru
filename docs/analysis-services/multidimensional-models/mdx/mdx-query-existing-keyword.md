---
title: "Ключевое слово EXISTING (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5078aa14be3c476e8b89545ed1541f12b7686f4e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-query---existing-keyword"></a>Запрос многомерных Выражений - ключевое слово EXISTING
  Указывает, что заданный набор должен вычисляться принудительно в текущем контексте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение набора.  
  
## <a name="remarks"></a>Замечания  
 По умолчанию наборы вычисляются в контексте куба, который содержит их элементы. Ключевое слово **Existing** указывает на то, что заданный набор должен вычисляться в текущем контексте.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается количество посредников, продажи которых снизились по сравнению с предыдущим периодом, на основании выбранных пользователем значений элемента State-Province, вычисленных с помощью функции **Aggregate** . Ключевое слово [Hierarchize (многомерные выражения)](../../../mdx/hierarchize-mdx.md) и [DrilldownLevel (многомерные выражения)](../../../mdx/drilldownlevel-mdx.md) используются для возвращения показателей падения продаж для категорий продуктов в измерении Product. Ключевое слово **Existing** заставляет функцию **Filter** вычислять набор в текущем контексте, то есть для элементов "Вашингтон" и "Орегон" в иерархии атрибутов State-Province.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
      (Filter  
         (Existing  
            (Reseller.Reseller.Reseller)  
         , [Measures].[Reseller Sales Amount] <   
            ([Measures].[Reseller Sales Amount]  
               ,[Date].Calendar.PrevMember  
            )  
        )  
      )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate   
      ( {[Geography].[State-Province].&[WA]&[US]  
         , [Geography].[State-Province].&[OR]&[US] }   
      )  
SELECT NON EMPTY HIERARCHIZE   
      (AddCalculatedMembers   
         (   
            {DrillDownLevel  
               ({[Product].[All Products]}  
               )  
            }   
         )   
      ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE   
      ( [Geography].[State-Province].x  
        , [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
        ,[Measures].[Declining Reseller Sales]  
      )  
  
```  
  
## <a name="see-also"></a>См. также  
 [Count (наборы) (многомерные выражения)](../../../mdx/count-set-mdx.md)   
 [AddCalculatedMembers &#40; Многомерные Выражения &#41;](../../../mdx/addcalculatedmembers-mdx.md)   
 [Статистическая функция &#40; Многомерные Выражения &#41;](../../../mdx/aggregate-mdx.md)   
 [Фильтр &#40; Многомерные Выражения &#41;](../../../mdx/filter-mdx.md)   
 [Свойства &#40; Многомерные Выражения &#41;](../../../mdx/properties-mdx.md)   
 [DrilldownLevel &#40; Многомерные Выражения &#41;](../../../mdx/drilldownlevel-mdx.md)   
 [Hierarchize &#40; Многомерные Выражения &#41;](../../../mdx/hierarchize-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../../../mdx/mdx-function-reference-mdx.md)  
  
  

