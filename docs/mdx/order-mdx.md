---
title: Order (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ORDER
dev_langs:
- kbMDX
helpviewer_keywords:
- Order function
ms.assetid: 84acff52-2443-4424-a09e-694e6f14c109
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f951c681b205ff9cfbc2b99c3935931811585186
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="order-mdx"></a>Order (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Замечания  
 **Порядок** функция может быть иерархической (в соответствии с помощью **ASC** или **DESC** флаг) или неиерархической (в соответствии с помощью **BASC** или **BDESC** флаг; **B** означает «break иерархии»). Если **ASC** или **DESC** указано, **порядок** функция сначала упорядочивает элементы согласно их положению в иерархии и затем выполняет сортировку каждого уровня. Если **BASC** или **BDESC** указано, **порядок** функция упорядочивает элементы в наборе, обращая внимания на иерархию. Указанный флаг **ASC** значение по умолчанию.  
  
 Если **порядок** функция используется с набором перекрестного соединения, в которых две или более иерархии и **DESC** флаг используется, только элементы последней иерархии в наборе упорядочены. В этом заключается отличие от версии служб Analysis Services 2000, где сортировались все иерархии в наборе.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается из **Adventure Works** куб, количество заказов посредников для всех календарных кварталов из иерархии «календарь» в измерении «дата». **Порядок** функция выполняет пересортировку набора по оси ROWS. **Порядок** функция сортирует набор по `[Reseller Order Count]` в иерархическом порядке, что определяется по убыванию `[Calendar]` иерархии.  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,DESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Обратите внимание как в этом примере при **DESC** флаг изменяется на **BDESC**, иерархия нарушается и список календарных кварталов возвращается без учета иерархии:  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,BDESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 В следующем примере возвращается мера Reseller Sales для пяти наиболее продаваемых подкатегорий товаров вне зависимости от иерархии, основываясь на значении меры Reseller Gross Profit. **Подмножества** функция используется для возвращения только первые пять кортежей в наборе после упорядочивания результата с помощью **порядок** функции.  
  
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
  
 В следующем примере используется **ранг** функции для упорядочивания элементов иерархии City на основе меры Reseller Sales Amount, а затем отображает их в упорядоченном виде. С помощью **порядок** функции для упорядочивания набора элементов иерархии City, сортировка выполняется только один раз и затем линейный просмотр перед его доставкой в отсортированном порядке.  
  
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
  
 Следующий пример возвращает количество продуктов в набор, являются уникальными, с помощью **порядок** функции для упорядочивания непустых кортежей перед вызовом **фильтра** функции. **CurrentOrdinal** функция используется для сравнения и удаления связей.  
  
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
  
 Чтобы понять, как **DESC** флаг работает с набором кортежей, сначала рассмотрите результаты следующего запроса:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 На оси строк можно увидеть, что группы территорий продаж отсортированы в убывающем порядке по элементу Tax Amount следующим образом: Северная Америка, Европа, Тихоокеанский регион, н/д. Теперь рассмотрим, что произойдет, если мы перекрестно соединить набор групп территорий продаж с набором подкатегорий продукции и применить **порядок** работать таким же образом, как показано ниже:  
  
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
  
 Во время упорядочивания набором подкатегорий продукции в порядке убывания, иерархические группы территорий продаж теперь не отсортированы и отображаются в порядке, они отображаются в иерархии: Европа, н/д, Северная Америка и Тихоокеанский регион. Это связано с тем, что сортируется только последняя иерархия в наборе кортежей, подкатегории продукции. Чтобы воспроизвести поведение служб Analysis Services 2000, используйте серию вложенных **формирования** функции для сортировки каждого набора до перекрестного соединения, например:  
  
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
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
