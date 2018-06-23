---
title: Ключевое слово EXISTING (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d7205cad36bbeb5adee16ca10bd881280b59d98f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194361"
---
# <a name="existing-keyword-mdx"></a>Ключевое слово EXISTING (многомерные выражения)
  Указывает, что заданный набор должен вычисляться принудительно в текущем контексте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение набора.  
  
## <a name="remarks"></a>Примечания  
 По умолчанию наборы вычисляются в контексте куба, который содержит их элементы. `Existing` Ключевое слово принудительно заданный набор должен вычисляться в текущем контексте.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается количество посредников, продажи которых снизились по сравнению с предыдущим периодом, на основании выбранных пользователем значений элемента State-Province, вычисленных с помощью функции `Aggregate`. Ключевое слово [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) и [DrilldownLevel (многомерные выражения)](/sql/mdx/drilldownlevel-mdx) используются для возвращения показателей падения продаж для категорий продуктов в измерении Product. `Existing` Силы ключевое слово set в `Filter` функции должен вычисляться в текущем контексте, то есть для элементов иерархии атрибута State-Province Вашингтон и Орегон.  
  
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
 [Число &#40;задать&#41; &#40;многомерных Выражений&#41;](/sql/mdx/count-set-mdx)   
 [AddCalculatedMembers &#40;многомерных Выражений&#41;](/sql/mdx/addcalculatedmembers-mdx)   
 [Агрегатные &#40;многомерных Выражений&#41;](/sql/mdx/aggregate-mdx)   
 [Фильтр &#40;многомерных Выражений&#41;](/sql/mdx/filter-mdx)   
 [Свойства &#40;многомерных Выражений&#41;](/sql/mdx/properties-mdx)   
 [DrilldownLevel &#40;многомерных Выражений&#41;](/sql/mdx/drilldownlevel-mdx)   
 [Hierarchize &#40;многомерных Выражений&#41;](/sql/mdx/hierarchize-mdx)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](/sql/mdx/mdx-function-reference-mdx)  
  
  
