---
title: Ключевое слово EXISTING (многомерные Выражения) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d41b49e4585d2a256250a009b09ffa9ed94ea925
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208733"
---
# <a name="mdx-query---existing-keyword"></a>Запрос многомерных выражений — ключевое слово Existing
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает, что заданный набор должен вычисляться принудительно в текущем контексте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение набора.  
  
## <a name="remarks"></a>Примечания  
 По умолчанию наборы вычисляются в контексте куба, который содержит их элементы. Ключевое слово **Existing** указывает на то, что заданный набор должен вычисляться в текущем контексте.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается количество посредников, продажи которых снизились по сравнению с предыдущим периодом, на основании выбранных пользователем значений элемента State-Province, вычисленных с помощью функции **Aggregate** . Ключевое слово [Hierarchize (многомерные выражения)](../../../mdx/hierarchize-mdx.md) и [DrilldownLevel (многомерные выражения)](../../../mdx/drilldownlevel-mdx.md) используются для возвращения показателей падения продаж для категорий продуктов в измерении Product. **Существующие** ключевое слово указывает на набор в **фильтра** функции, который будет вычисляться в текущем контексте, то есть для Вашингтона и Орегона элементы иерархии атрибута State-Province.  
  
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
 [AddCalculatedMembers (многомерные выражения)](../../../mdx/addcalculatedmembers-mdx.md)   
 [Aggregate (многомерные выражения)](../../../mdx/aggregate-mdx.md)   
 [Filter (многомерные выражения)](../../../mdx/filter-mdx.md)   
 [Properties (многомерные выражения)](../../../mdx/properties-mdx.md)   
 [DrilldownLevel (многомерные выражения)](../../../mdx/drilldownlevel-mdx.md)   
 [Hierarchize (многомерные выражения)](../../../mdx/hierarchize-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../../../mdx/mdx-function-reference-mdx.md)  
  
  
