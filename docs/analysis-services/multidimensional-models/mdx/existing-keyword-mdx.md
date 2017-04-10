---
title: "Ключевое слово EXISTING (многомерные выражения) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXISTING"
helpviewer_keywords: 
  - "Existing, ключевое слово"
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
caps.latest.revision: 38
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Ключевое слово EXISTING (многомерные выражения)
  Указывает, что заданный набор должен вычисляться принудительно в текущем контексте.  
  
## Синтаксис  
  
```  
  
Existing Set_Expression  
```  
  
## Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение набора.  
  
## Замечания  
 По умолчанию наборы вычисляются в контексте куба, который содержит их элементы. Ключевое слово **Existing** указывает на то, что заданный набор должен вычисляться в текущем контексте.  
  
## Пример  
 В следующем примере возвращается количество посредников, продажи которых снизились по сравнению с предыдущим периодом, на основании выбранных пользователем значений элемента State-Province, вычисленных с помощью функции **Aggregate**. Функции [Hierarchize (многомерные выражения)](../../../mdx/hierarchize-mdx.md) и [DrilldownLevel (многомерные выражения)](../../../mdx/drilldownlevel-mdx.md) используются для возвращения показателей падения продаж для категорий продуктов в измерении Product. Ключевое слово **Existing** заставляет функцию **Filter** вычислять набор в текущем контексте, то есть для элементов "Вашингтон" и "Орегон" в иерархии атрибутов State-Province.  
  
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
  
## См. также  
 [Count (наборы) (многомерные выражения)](../../../mdx/count-set-mdx.md)   
 [AddCalculatedMembers (многомерные выражения)](../../../mdx/addcalculatedmembers-mdx.md)   
 [Aggregate (многомерные выражения)](../../../mdx/aggregate-mdx.md)   
 [Filter (многомерные выражения)](../../../mdx/filter-mdx.md)   
 [Properties (многомерные выражения)](../../../mdx/properties-mdx.md)   
 [DrilldownLevel (многомерные выражения)](../../../mdx/drilldownlevel-mdx.md)   
 [Hierarchize (многомерные выражения)](../../../mdx/hierarchize-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../../../mdx/mdx-function-reference-mdx.md)  
  
  