---
title: Ключевое слово EXISTING (многомерные выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a6c5e8dbe3e1b1ad44286bcbb79132010cad618a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66073968"
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
  
## <a name="remarks"></a>Remarks  
 По умолчанию наборы вычисляются в контексте куба, который содержит их элементы. Ключевое слово `Existing` указывает на то, что заданный набор должен вычисляться в текущем контексте.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается количество посредников, продажи которых снизились по сравнению с предыдущим периодом, на основании выбранных пользователем значений элемента State-Province, вычисленных с помощью функции `Aggregate`. Ключевое слово [Hierarchize (многомерные выражения)](/sql/mdx/hierarchize-mdx) и [DrilldownLevel (многомерные выражения)](/sql/mdx/drilldownlevel-mdx) используются для возвращения показателей падения продаж для категорий продуктов в измерении Product. `Existing` Ключевое слово заставляет набор в `Filter` функции вычисляться в текущем контексте, т. е. для элементов Вашингтон и Орегон иерархии атрибута «Штат-провинция».  
  
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
 [Count &#40;Set&#41; &#40;многомерных выражений&#41;](/sql/mdx/count-set-mdx)   
 [AddCalculatedMembers &#40;&#41;многомерных выражений](/sql/mdx/addcalculatedmembers-mdx)   
 [Статистическая обработка &#40;многомерных выражений&#41;](/sql/mdx/aggregate-mdx)   
 [Фильтрация &#40;&#41;многомерных выражений](/sql/mdx/filter-mdx)   
 [Свойства &#40;&#41;многомерных выражений](/sql/mdx/properties-mdx)   
 [DrilldownLevel &#40;&#41;многомерных выражений](/sql/mdx/drilldownlevel-mdx)   
 [Hierarchize &#40;&#41;многомерных выражений](/sql/mdx/hierarchize-mdx)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](/sql/mdx/mdx-function-reference-mdx)  
  
  
