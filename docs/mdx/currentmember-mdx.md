---
title: "CurrentMember (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CURRENTMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- CurrentMember function
ms.assetid: 5da76496-7d13-4f17-9cee-3e1ef70c2d97
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 068d7219727c1187e5c0c06509cfdec3fe189fa2
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="currentmember-mdx"></a>CurrentMember (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает текущий элемент указанной иерархии во время итерации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Hierarchy_Expression.CurrentMember  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Expression*  
 Допустимое многомерное выражение, возвращающее иерархию.  
  
## <a name="remarks"></a>Замечания  
 Текущим называется элемент, над которым выполняется операция на данном шаге итерации по набору элементов иерархии. **CurrentMember** функция возвращает этот элемент.  
  
> [!IMPORTANT]  
>  Если измерение содержит единственную видимую иерархию, на нее можно сослаться по имени измерения или по имени иерархии, поскольку имя измерения разрешается в единственную видимую иерархию. Например, многомерное выражение `Measures.CurrentMember` является допустимым, поскольку измерение Measures разрешается в единственную видимую иерархию.  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показано, как **Currentmember** можно использовать для поиска текущего элемента из столбцов, строк и осей среза в иерархии:  
  
 `WITH MEMBER MEASURES.CURRENTDATE AS`  
  
 `[Date].[Calendar].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.CURRENTPRODUCT AS`  
  
 `[Product].[Product Categories].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.CURRENTMEASURE AS`  
  
 `MEASURES.CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.CURRENTCUSTOMER AS`  
  
 `[Customer].[Customer Geography].CURRENTMEMBER.NAME`  
  
 `SELECT`  
  
 `[Product].[Product Categories].[Category].MEMBERS`  
  
 `*`  
  
 `{MEASURES.CURRENTDATE, MEASURES.CURRENTPRODUCT,MEASURES.CURRENTMEASURE, MEASURES.CURRENTCUSTOMER}`  
  
 `ON 0,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Customer].[Customer Geography].[Country].&[Australia])`  
  
 Изменяется текущий элемент иерархии, используемой по оси в запросе. Таким образом можно также изменить текущий элемент других иерархий того же измерения, которые не используются на оси; Такое поведение называется «автоматическим существованием» и Дополнительные сведения можно найти в [основные понятия многомерных Выражений &#40; Службы Analysis Services &#41; ](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md). Например, приведенный ниже запрос показывает, как текущий элемент иерархии «Календарный год» измерения «Дата» изменяется вместе с текущим элементом иерархии «Календарь», когда последняя отображается по оси строк:  
  
 `WITH MEMBER MEASURES.CURRENTYEAR AS`  
  
 `[Date].[Calendar Year].CURRENTMEMBER.NAME`  
  
 `SELECT`  
  
 `{MEASURES.CURRENTYEAR}`  
  
 `ON 0,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 **CurrentMember** очень важен для вычислений с учетом контекста запроса, они используются. В следующем примере возвращается количество заказов по каждому продукту и процентная доля заказов по категориям и моделям, из **Adventure Works** куба. **CurrentMember** функция определяет продукт, количество заказа будет использоваться во время вычисления.  
  
```  
WITH   
   MEMBER [Measures].[Order Percent by Category] AS  
   CoalesceEmpty  
(   
      ([Product].[Product Categories].CurrentMember,  
        Measures.[Order Quantity]) /   
          (  
           Ancestor  
           ( [Product].[Product Categories].CurrentMember,   
             [Product].[Product Categories].[Category]  
           ), Measures.[Order Quantity]  
       ), 0  
   ), FORMAT_STRING='Percent'  
SELECT   
   {Measures.[Order Quantity],  
      [Measures].[Order Percent by Category]} ON COLUMNS,  
{[Product].[Product].Members} ON ROWS  
FROM [Adventure Works]  
WHERE {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

