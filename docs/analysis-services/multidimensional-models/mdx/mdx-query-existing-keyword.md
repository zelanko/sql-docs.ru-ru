---
title: Ключевое слово EXISTING (многомерные Выражения) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 08cdfd62f25ec42195418938da37c502f221120d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="mdx-query---existing-keyword"></a>Запрос многомерных Выражений - ключевое слово EXISTING
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Число & #40; Выбрать & #41; & #40; Многомерные Выражения & #41;](../../../mdx/count-set-mdx.md)   
 [AddCalculatedMembers & #40; Многомерные Выражения & #41;](../../../mdx/addcalculatedmembers-mdx.md)   
 [Статистическая функция & #40; Многомерные Выражения & #41;](../../../mdx/aggregate-mdx.md)   
 [Фильтр & #40; Многомерные Выражения & #41;](../../../mdx/filter-mdx.md)   
 [Свойства & #40; Многомерные Выражения & #41;](../../../mdx/properties-mdx.md)   
 [DrilldownLevel & #40; Многомерные Выражения & #41;](../../../mdx/drilldownlevel-mdx.md)   
 [Hierarchize & #40; Многомерные Выражения & #41;](../../../mdx/hierarchize-mdx.md)   
 [Справочник по функциям многомерных Выражений & #40; Многомерные Выражения & #41;](../../../mdx/mdx-function-reference-mdx.md)  
  
  
