---
title: Hierarchize (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8ab2c866f201c53684c316282a143b4f672cb8e9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68105434"
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
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
