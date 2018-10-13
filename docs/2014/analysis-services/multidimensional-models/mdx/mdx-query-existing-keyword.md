---
title: Ключевое слово EXISTING (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ceaeac711ed30028dab3bc09827df9b6ae1f0e0a
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/10/2018
ms.locfileid: "48905974"
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
 По умолчанию наборы вычисляются в контексте куба, который содержит их элементы. Ключевое слово `Existing` указывает на то, что заданный набор должен вычисляться в текущем контексте.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается количество посредников, продажи которых снизились по сравнению с предыдущим периодом, на основании выбранных пользователем значений элемента State-Province, вычисленных с помощью функции `Aggregate`. Ключевое слово [Hierarchize (многомерные выражения)](/sql/mdx/hierarchize-mdx) и [DrilldownLevel (многомерные выражения)](/sql/mdx/drilldownlevel-mdx) используются для возвращения показателей падения продаж для категорий продуктов в измерении Product. `Existing` Ключевое слово указывает на набор в `Filter` функции, который будет вычисляться в текущем контексте, то есть для Вашингтона и Орегона элементы иерархии атрибута State-Province.  
  
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
 [Count (наборы) (многомерные выражения)](/sql/mdx/count-set-mdx)   
 [AddCalculatedMembers (многомерные выражения)](/sql/mdx/addcalculatedmembers-mdx)   
 [Aggregate (многомерные выражения)](/sql/mdx/aggregate-mdx)   
 [Filter (многомерные выражения)](/sql/mdx/filter-mdx)   
 [Properties (многомерные выражения)](/sql/mdx/properties-mdx)   
 [DrilldownLevel (многомерные выражения)](/sql/mdx/drilldownlevel-mdx)   
 [Hierarchize (многомерные выражения)](/sql/mdx/hierarchize-mdx)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](/sql/mdx/mdx-function-reference-mdx)  
  
  
