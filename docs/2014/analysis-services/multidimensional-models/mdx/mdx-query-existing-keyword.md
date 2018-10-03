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
ms.openlocfilehash: 8431c4b29f20b3c87e3b944736612d009426900a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106554"
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
 В следующем примере возвращается количество посредников, продажи которых снизились по сравнению с предыдущим периодом, на основании выбранных пользователем значений элемента State-Province, вычисленных с помощью функции `Aggregate`. Ключевое слово [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) и [DrilldownLevel (многомерные выражения)](/sql/mdx/drilldownlevel-mdx) используются для возвращения показателей падения продаж для категорий продуктов в измерении Product. `Existing` Силы ключевое слово set в `Filter` функции, который будет вычисляться в текущем контексте, то есть для Вашингтона и Орегона элементы иерархии атрибута State-Province.  
  
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
  
  
