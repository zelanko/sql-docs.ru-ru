---
title: Order (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d540b299fd08aa78576b19040a4cfafb9046ae7c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68055679"
---
# <a name="order-mdx"></a>Order (многомерные выражения)


  Упорядочивает элементы указанного набора, по выбору сохраняя или нарушая иерархию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Numeric expression syntax  
Order(Set_Expression, Numeric_Expression   
[ , { ASC | DESC | BASC | BDESC } ] )  
  
String expression syntax  
Order(Set_Expression, String_Expression   
[ , { ASC | DESC | BASC | BDESC } ] )  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
 *String_Expression*  
 Допустимое строковое выражение (обычно многомерное выражение над координатами ячейки), возвращающее число, представленное в виде строки.  
  
## <a name="remarks"></a>Remarks  
 Функция **Order** может быть иерархической (как указано с помощью флага **ASC** или **DESC** ) или неиерархического (как указано с помощью флага **Basc** или **BDESC** ; **B** означает «разбить иерархию»). Если указано **ASC** или **DESC** , функция **Order** сначала упорядочивает элементы в соответствии с их позицией в иерархии, а затем упорядочивает каждый уровень. Если указано **Basc** или **BDESC** , функция **Order** упорядочивает элементы в наборе без учета иерархии. Если флаг не указан, по умолчанию используется значение **ASC** .  
  
 Если функция **Order** используется с набором, в котором перекрестно Соединенных две или более иерархии, и используется флаг **DESC** , упорядочиваются только элементы последней иерархии в наборе. В этом заключается отличие от версии служб Analysis Services 2000, где сортировались все иерархии в наборе.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается из куба **Adventure Works** число заказов торгового посредника за все календарные кварталы из иерархии Calendar в измерении Date. Функция **Order** переупорядочивает набор для оси ROWS. Функция **Order** упорядочивает набор по `[Reseller Order Count]` убыванию в иерархическом порядке, определенном `[Calendar]` иерархией.  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,DESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Обратите внимание, как в этом примере при изменении флага **DESC** на **BDESC**иерархия будет нарушена, а список кварталов в календаре возвращается без учета для иерархии.  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,BDESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 В следующем примере возвращается мера Reseller Sales для пяти наиболее продаваемых подкатегорий товаров вне зависимости от иерархии, основываясь на значении меры Reseller Gross Profit. Функция **подмножества** используется для возвращения только первых 5 кортежей в наборе после упорядочивания результата с помощью функции **Order** .  
  
 `SELECT Subset`  
  
 `(Order`  
  
 `([Product].[Product Categories].[SubCategory].members`  
  
 `,[Measures].[Reseller Gross Profit]`  
  
 `,BDESC`  
  
 `)`  
  
 `,0`  
  
 `,5`  
  
 `) ON 0`  
  
 `FROM [Adventure Works]`  
  
 В следующем примере функция **Rank** используется для ранжирования элементов иерархии City на основе меры Товарооборот посредников, а затем отображает их в порядке ранжирования. При использовании функции **Order** для предварительного упорядочения набора элементов иерархии City сортировка выполняется только один раз, а затем выполняется линейное сканирование, прежде чем будет представлен порядок сортировки.  
  
```  
WITH   
SET OrderedCities AS Order  
   ([Geography].[City].[City].members  
   , [Measures].[Reseller Sales Amount], BDESC  
   )  
MEMBER [Measures].[City Rank] AS Rank  
   ([Geography].[City].CurrentMember, OrderedCities)  
SELECT {[Measures].[City Rank],[Measures].[Reseller Sales Amount]}  ON 0   
,Order  
   ([Geography].[City].[City].MEMBERS  
   ,[City Rank], ASC)  
    ON 1  
FROM [Adventure Works]  
```  
  
 В следующем примере возвращается количество продуктов в наборе, уникальных, с помощью функции **Order** для упорядочивания непустых кортежей перед использованием функции **Filter** . Функция **CurrentOrdinal** используется для сравнения и исключения связей.  
  
```  
WITH MEMBER [Measures].[PrdTies] AS Count  
   (Filter  
      (Order  
        (NonEmpty  
          ([Product].[Product].[Product].Members  
          , {[Measures].[Reseller Order Quantity]}  
          )  
       , [Measures].[Reseller Order Quantity]  
       , BDESC  
       ) AS OrdPrds  
    , (OrdPrds.CurrentOrdinal < OrdPrds.Count   
       AND [Measures].[Reseller Order Quantity] =   
          ( [Measures].[Reseller Order Quantity]  
            , OrdPrds.Item  
               (OrdPrds.CurrentOrdinal  
               )  
            )  
         )  
         OR (OrdPrds.CurrentOrdinal > 1   
            AND [Measures].[Reseller Order Quantity] =   
               ([Measures].[Reseller Order Quantity]  
               , OrdPrds.Item  
                  (OrdPrds.CurrentOrdinal-2)  
                )  
             )  
          )  
       )  
SELECT {[Measures].[PrdTies]} ON 0  
FROM [Adventure Works]  
```  
  
 Чтобы понять, как флаг **DESC** работает с наборами кортежей, сначала рассмотрим результаты следующего запроса:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 На оси строк можно увидеть, что группы территории продаж упорядочены в порядке убывания по сумме налогов: Северная Америка, Европа, тихоокеанское время, НД. Теперь посмотрим, что произойдет, если перечислить набор групп территории продаж с помощью набора подкатегорий продуктов и применить функцию **Order** таким же образом, как показано ниже:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
*  
{[Product].[Product Categories].[subCategory].Members}  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 Хотя набор подкатегорий продуктов упорядочен в порядке убывания, группы территории продаж теперь не сортируются и отображаются в том порядке, в котором они отображаются в иерархии: Европа, NA, Северная Америка и Тихоокеанский регион. Это связано с тем, что сортируется только последняя иерархия в наборе кортежей, подкатегории продукции. Чтобы воспроизвести поведение Analysis Services 2000, используйте ряд вложенных функций **Generate** для сортировки каждого набора, прежде чем он будет перекрестно Соединенных, например:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
GENERATE(  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
,  
ORDER(  
[Sales Territory].[Sales Territory].CURRENTMEMBER  
*  
{[Product].[Product Categories].[subCategory].Members}  
,[Measures].[Tax Amount], DESC))  
ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
