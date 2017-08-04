---
title: "Descendants (многомерные Выражения) | Документы Microsoft"
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
- DESCENDANTS
dev_langs:
- kbMDX
helpviewer_keywords:
- Descendants function
ms.assetid: d103b0f5-e794-4828-aa57-43f6918a0749
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 82ae4fdab005443b03802f443097ddb435342c1a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="descendants-mdx"></a>Descendants (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает набор потомков элемента на указанном уровне или расстоянии, по желанию включая или исключая потомков на других уровнях.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member expression syntax using a level expression  
Descendants(Member_Expression [ , Level_Expression [ ,Desc_Flag ] ] )  
  
Member expression syntax using a numeric expression  
Descendants(Member_Expression [ , Distance [ ,Desc_Flag ] ] )  
  
Set expression syntax using a level expression  
Descendants(Set_Expression [ , Level_Expression [ ,Desc_Flag ] ] )  
  
Member expression syntax using a numeric expression  
Descendants(Set_Expression [ , Distance [ ,Desc_Flag ] ] )  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Расстояние*  
 Допустимое числовое выражение, указывающее расстояние от заданного элемента.  
  
 *Desc_Flag*  
 Допустимая строка выражения, указывающая описание флага, коррелирующего с возможными наборами потомков.  
  
## <a name="remarks"></a>Замечания  
 Если уровень указан, **потомков** функция возвращает набор, содержащий потомки заданного элемента или элементы заданного набора на заданном уровне, выборочно изменяемом при помощи флага, определенного в *Desc_Flag*.  
  
 Если *расстояние* указано, **потомков** функция возвращает набор, содержащий потомки заданного элемента или элементы заданного набора, заданного количество уровней вне иерархии заданного элемента, выборочно изменяемом при помощи флага, определенного в *Desc_Flag*. Обычно эта функция используется с аргументом Distance для распределения неоднородных иерархий. Если заданное расстояние равно нулю, то функция возвращает набор, состоящий только из заданного элемента или заданного набора.  
  
 Если указано выражение набора, **потомков** функции разрешается отдельно для каждого элемента набора и набор создается заново. Другими словами, синтаксис, используемый для **потомков** является функциональным эквивалентом многомерных Выражений функция [формирования](../mdx/generate-mdx.md) функции.  
  
 Если задан уровень или расстояние, значение по умолчанию для уровня, используемые функцией определяется путем вызова [уровень](../mdx/level-mdx.md) функция (<\<член >>. Уровня) для указанного элемента (если элемент определен) или путем вызова **уровень** функции для каждого элемента заданного набора (если набор определен). Если выражение уровня, расстояние и флаги не определены, то функция будет выполнена только в случае использования следующего синтаксиса:  
  
 `Descendants`  
  
 `(`  
  
 `Member_Expression ,`  
  
 `Member_Expression.Level ,`  
  
 `SELF_BEFORE_AFTER`  
  
 `)`  
  
 Если уровень определен, а описание флага не определено, то функция будет выполнена только в случае использования следующего синтаксиса:  
  
 `Descendants`  
  
 `(`  
  
 `Member_Expression ,`  
  
 `Level_Expression,`  
  
 `SELF`  
  
 `)`  
  
 Изменяя значение аргумента описания флага, можно включать или исключать на указанном уровне или расстоянии потомки, находящиеся до указанного уровня или расстояния (вплоть до конечных узлов) и после, а также конечные потомки независимо от указанного уровня или расстояния. В следующей таблице описаны допустимые флаги *Desc_Flag* аргумент.  
  
|Флаг|Description|  
|----------|-----------------|  
|SELF|Возвращает только потомки заданного уровня или на заданном расстоянии. Функция включает в себя заданный элемент, если заданный уровень является уровнем заданного элемента.|  
|AFTER|Возвращает потомки со всех уровней, подчиненных уровню аргумента расстояния.|  
|BEFORE|Возвращает потомки элементов со всех уровней между заданным элементом и заданным уровнем или на заданном расстоянии. Включает в себя заданный элемент, но не включает элементы заданного уровня или расстояния.|  
|BEFORE_AND_AFTER|Возвращает потомки элементов со всех уровней, зависящих от заданного уровня или заданного элемента. Включает в себя заданный элемент, но не включает элементы заданного уровня или расстояния.|  
|SELF_AND_AFTER|Возвращает потомки элементов заданного уровня или расстояния и все уровни, зависящие от заданного уровня или расстояния.|  
|SELF_AND_BEFORE|Возвращает потомки заданного уровня или расстояния и со всех уровней между заданным элементом и заданным уровнем или на заданном расстоянии, включая заданный элемент.|  
|SELF_BEFORE_AFTER|Возвращает потомки со всех уровней, зависящих от уровня заданного элемента, и включает заданный элемент.|  
|LEAVES|Возвращает конечные потомки элементов между заданным элементом и заданным уровнем или на заданном расстоянии.|  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается заданный элемент (United States) и элементы между заданным элементом и элементами уровня, предшествующего заданному (City). В примере возвращаются сам заданный элемент (United States) и элементы уровня State-Province (уровень перед уровнем City). Данный пример включает в себя комментарии к аргументам, что позволяет легко проверить другие аргументы для этой функции.  
  
```  
SELECT Descendants  
   ([Geography].[Geography].[Country].&[United States]  
      //, [Geography].[Geography].[Country]  
   , [Geography].[Geography].[City]  
      //, [Geography].[Geography].Levels (3)  
      //, SELF   
      //, AFTER  
      , BEFORE  
      // BEFORE_AND_AFTER  
      //, SELF_AND_AFTER  
      //, SELF_AND_BEFORE  
      //,SELF_BEFORE_AFTER  
      //,LEAVES   
   ) ON 0  
FROM [Adventure Works]   
```  
  
 В следующем примере возвращается среднее ежедневное значение `Measures.[Gross Profit Margin]` меры по всем дням всех месяцев 2003 финансового года, вычисленный на основе **Adventure Works** куба. **Потомков** функция возвращает набор дней, определяемый из текущего элемента `[Date].[Fiscal]` иерархии.  
  
```  
WITH MEMBER Measures.[Avg Gross Profit Margin] AS Avg  
   (  
      Descendants( [Date].[Fiscal].CurrentMember,   
           [Date].[Fiscal].[Date]  
          ),   
        Measures.[Gross Profit Margin]  
   )  
SELECT  
   Measures.[Avg Gross Profit Margin] ON COLUMNS,  
   [Date].[Fiscal].[Month].Members ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Fiscal Year].&[2003])  
```  
  
 В следующем примере используется выражение уровня и возвращается мера Internet Sales Amount для каждой административно-территориальной единицы (мера State-Province) Австралии (Australia), возвращается также процентное соотношение относительно общего значения Internet Sales Amount для каждой территории (State-Province). В этом примере используется функция Item для извлечения первый (и единственный) кортежа из набора, возвращаемого **предков** функции.  
  
```  
WITH MEMBER Measures.x AS   
   [Measures].[Internet Sales Amount] /   
   ( [Measures].[Internet Sales Amount],  
      Ancestors   
         ( [Customer].[Customer Geography].CurrentMember,   
           [Customer].[Customer Geography].[Country]  
         ).Item (0)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{Descendants   
   ( [Customer].[Customer Geography].[Country].&[Australia],   
     [Customer].[Customer Geography].[State-Province], SELF   
   )    
} ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

