---
title: Sum (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eb4e9d55ef2228404dd9113170066e4a3612a0a1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036674"
---
# <a name="sum-mdx"></a>Sum (многомерные выражения)


  Возвращает сумму числового выражения, вычисленную по указанному набору.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Sum( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение набора.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Remarks  
 Если числовое выражение указано, его значение вычисляется для всех элементов набора, затем эти значения суммируются. Если числовое выражение не указано, вычисления выполняются в текущем контексте элементов, затем значения суммируются. Если функция SUM применяется к нечисловому выражению, результат не определен.  
  
> [!NOTE]  
>  Службы Analysis Services пропускают значения NULL при вычислении суммы набора чисел.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается сумма мер Reseller Sales Amounts для всех элементов в иерархии атрибута Product.Category в 2001 и 2002 календарном году.  
  
```  
WITH MEMBER Measures.x AS SUM  
   ( { [Date].[Calendar Year].&[2001]  
         , [Date].[Calendar Year].&[2002] }  
      , [Measures].[Reseller Sales Amount]  
    )  
SELECT Measures.x ON 0  
,[Product].[Category].Members ON 1  
FROM [Adventure Works]  
```  
  
 В следующем примере возвращается сумма затрат на транспортировку товаров, заказанных через Интернет, за июль 2002 года, до 20 июля.  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере используется ключевое слово WITH MEMBER и функция **Sum** для определения вычисляемого элемента в измерении Measures, содержащего сумму меры Товарооборот посредников для канады и США элементов иерархии атрибута Country в измерении Geography.  
  
```  
WITH MEMBER Measures.NorthAmerica AS SUM   
      (  
         {[Geography].[Country].&[Canada]  
            , [Geography].[Country].&[United States]}  
       ,[Measures].[Reseller Sales Amount]  
      )  
SELECT {[Measures].[NorthAmerica]} ON 0,  
[Product].[Category].members ON 1  
FROM [Adventure Works]  
```  
  
 Часто функция **Sum** используется с функцией **CurrentMember** или функциями, такими как **YTD** , которые возвращают набор, который зависит от CurrentMember иерархии. Например, приведенный ниже запрос возвращает сумму меры Internet Sales Amount для всех дат с начала календарного года до даты, отображенной по оси строк:  
  
 `WITH MEMBER MEASURES.YTDSUM AS`  
  
 `SUM(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDSUM} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
