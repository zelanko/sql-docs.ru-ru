---
title: Order (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 43a75f4a42193c231c1acc710512b05537675991
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63277848"
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
  
## <a name="remarks"></a>Примечания  
 **Порядок** функция может быть иерархической (как указано с помощью **ASC** или **DESC** флаг) или неиерархической (как указано с помощью **BASC**  или **BDESC** флаг; **B** означает «break иерархия»). Если **ASC** или **DESC** указано, **порядок** функция сначала упорядочивает элементы согласно их положению в иерархии и затем выполняет сортировку каждого уровня. Если **BASC** или **BDESC** указано, **порядок** функция упорядочивает элементы в наборе, обращая внимания на иерархию. Указанный флаг **ASC** используется по умолчанию.  
  
 Если **порядок** функция используется с набором, в которых два или более иерархии перекрестного соединения и **DESC** флаг используется, только элементы последней иерархии в наборе упорядочены. В этом заключается отличие от версии служб Analysis Services 2000, где сортировались все иерархии в наборе.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается из **Adventure Works** куба, количество заказов посредников для всех календарных кварталов из иерархии «календарь» в измерении Date. **Порядок** функция выполняет пересортировку набора по оси ROWS. **Порядок** функция упорядочивает набор по `[Reseller Order Count]` в иерархическом порядке, определенном по убыванию `[Calendar]` иерархии.  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,DESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Обратите внимание, что как в этом примере при **DESC** флаг изменяется на **BDESC**, иерархия нарушается и список календарных кварталов возвращается без учета того, для иерархии:  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,BDESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 В следующем примере возвращается мера Reseller Sales для пяти наиболее продаваемых подкатегорий товаров вне зависимости от иерархии, основываясь на значении меры Reseller Gross Profit. **Подмножества** функция используется для возврата только первые пять кортежей в наборе после упорядочивания результата с помощью **порядок** функции.  
  
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
  
 В следующем примере используется **ранг** функции для упорядочивания элементов иерархии City на основании меры Reseller Sales Amount и затем отображает их в упорядоченном. С помощью **порядок** функцию в порядке старшинства набор элементов иерархии City, сортировка сделать только один раз и затем следуют линейный Просмотр, прежде чем представляемых в отсортированном порядке.  
  
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
  
 Следующий пример возвращает количество продуктов в наборе, являются уникальными, с помощью **порядок** функции для упорядочивания непустых кортежей перед вызовом **фильтра** функции. **CurrentOrdinal** функция используется для сравнения и удаления связей.  
  
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
  
 Чтобы понять, каким образом **DESC** флаг работает с набором кортежей, сначала рассмотрите результаты следующего запроса:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 По оси строк можно увидеть, что группы территорий продаж отсортированы в убывающем порядке по элементу Tax Amount следующим образом: Северная Америка, Европа, Тихоокеанский регион Теперь рассмотрим, что произойдет, если мы перекрестно соединить набор групп территорий продаж с набором подкатегорий продукции и применить **порядок** функции так же, как показано ниже:  
  
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
  
 Хотя набором подкатегорий продукции товара в порядке убывания, иерархические группы территорий продаж теперь не отсортированы и отображаются в порядке их следования в иерархии: Европа, н/д, Северная Америка и Тихоокеанский. Это связано с тем, что сортируется только последняя иерархия в наборе кортежей, подкатегории продукции. Чтобы воспроизвести поведение служб Analysis Services 2000, использовать серию вложенных **формирования** функции для сортировки каждого набора до перекрестного соединения, например:  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
