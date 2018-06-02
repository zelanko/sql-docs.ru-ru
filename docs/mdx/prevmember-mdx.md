---
title: PrevMember (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1c71a64e9fc336c308e32968dc702c926a9f7731
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582256"
---
# <a name="prevmember-mdx"></a>PrevMember (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает предыдущий элемент уровня, содержащего указанный элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.PrevMember   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 **PrevMember** функция возвращает предыдущий элемент на том же уровне, что и указанный элемент.  
  
## <a name="example"></a>Пример  
 В примере показан простой запрос, который использует **PrevMember** функцию для отображения имени элемента сразу после текущего элемента по оси строк:  
  
 `WITH MEMBER MEASURES.PREVMEMBERDEMO AS`  
  
 `[Date].[Calendar].CURRENTMEMBER.PREVMEMBER.NAME`  
  
 `SELECT MEASURES.PREVMEMBERDEMO ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 В следующем примере возвращается количество посредников, продажи которых снизились по сравнению с предыдущим периодом, на основании выбранных пользователем значений элемента State-Province, вычисленных с помощью агрегатной функции. **Hierarchize** и **DrillDownLevel** функции используются для возвращения показателей падения продаж для категорий продуктов в измерении Product. **PrevMember** функция используется для сравнения текущего периода времени с предыдущим периодом.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS   
   Count(  
      Filter(  
         Existing(Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
            )  
         )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate (   
      {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
         )  
SELECT NON EMPTY Hierarchize (  
   AddCalculatedMembers (  
      {DrillDownLevel({[Product].[All Products]})}  
         )  
   )  
        DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
    [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
    [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
