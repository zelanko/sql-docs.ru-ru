---
description: Hierarchize (многомерные выражения)
title: Hierarchize (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3c1683819420d150e2f9b330ba94bc9e228d167f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429916"
---
# <a name="hierarchize-mdx"></a>Hierarchize (многомерные выражения)


  Упорядочивает элементы набора в иерархии.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchize(Set_Expression [ , POST ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Remarks  
 Функция **Hierarchize** упорядочивает элементы указанного набора в иерархическом порядке. Повторяющиеся элементы всегда сохраняются.  
  
-   Если параметр **POST** не указан, функция сортирует элементы на уровне в естественном порядке. Естественным порядком является порядок следования элементов в иерархии по умолчанию, если не заданы другие условия сортировки. Потомки следуют сразу после своих предков.  
  
-   Если указан параметр **POST** , функция **Hierarchize** сортирует элементы на уровне, используя порядок после естественного. Другими словами, дочерние элементы предшествуют своим родителям.  
  
## <a name="example"></a>Пример  
 В следующем примере детализируется обобщением элемент Canada. Функция **Hierarchize** используется для упорядочивания указанных элементов набора в иерархическом порядке, который требуется для функции **DrillupMember** .  
  
```  
SELECT DrillUpMember   
   (  
      Hierarchize  
         (  
            {[Geography].[Geography].[Country].[Canada]  
            ,[Geography].[Geography].[Country].[United States]  
            ,[Geography].[Geography].[State-Province].[Alberta]  
            ,[Geography].[Geography].[State-Province].[Brunswick]  
            ,[Geography].[Geography].[State-Province].[Colorado]   
            }  
         ), {[Geography].[Geography].[Country].[United States]}  
   )  
ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере возвращается сумма `Measures.[Order Quantity]` элемента, агрегированная за первые девять месяцев 2003, содержащихся в `Date` измерении, из куба **Adventure Works** . Функция **PeriodsToDate** определяет кортежи в наборе, для которого работает агрегатная функция. Функция **Hierarchize** упорядочивает элементы указанного набора элементов из измерения Product в иерархическом порядке.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
