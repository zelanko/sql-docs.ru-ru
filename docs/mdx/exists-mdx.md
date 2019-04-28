---
title: EXISTS (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b53932676cae30e4b1111c785a6a78c992a3685
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62690861"
---
# <a name="exists-mdx"></a>Exists (многомерные выражения)


  Возвращает набор кортежей первого указанного набора, которые один или более раз встречаются во втором наборе. Эта функция вручную выполняет операцию автоматической проверки. Дополнительные сведения об автоматической проверке, см. в разделе [основные понятия многомерных Выражений &#40;служб Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
 Если необязательный \<имя группы мер > не указан, функция возвращает кортежи, встречающиеся один или несколько кортежей второго набора и кортежи, с которыми связаны строк в таблице фактов заданной группы мер.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Exists( Set_Expression1 , Set_Expression2 [, MeasureGroupName] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *MeasureGroupName*  
 Допустимое строковое выражение, обозначающее имя группы мер.  
  
## <a name="remarks"></a>Примечания  
  
1.  Строки группы мер, содержащих значения null, участие в разработке **Exists** Если указан аргумент MeasureGroupName. Это различие между Эта форма Exists и функцию Nonempty: Если свойство NullProcessing данных мер имеет значение Preserve, это означает, что меры будут показывать значения Null, при выполнении запросов для данной части куба; NonEmpty всегда будет удалять кортежи из набора, имеющим значение Null меры, тогда как Exists с аргументом MeasureGroupName не будет отфильтровывать кортежи со связанными строками групп мер, даже если меры имеют значения Null.  
  
2.  Если *MeasureGroupName* используется параметр, результат будет зависеть, есть ли видимых мер в ссылочной группе мер; Если есть нет видимых мер в ссылочной группе мер EXISTS всегда возвращает пустой набор, независимо от значений *Set_Expression1* и *Set_Expression2*.  
  
## <a name="examples"></a>Примеры  
 Клиенты, проживающие в Калифорнии:  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Customer].[State-Province].&[CA]&[US]}  
) ON 1   
FROM [Adventure Works]  
  
```  
  
 Клиенты, проживающие в Калифорнии и совершившие сделки:  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Customer].[State-Province].&[CA]&[US]}  
, "Internet Sales") ON 1   
FROM [Adventure Works]  
  
```  
  
 Клиенты, совершившие сделки:  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, , "Internet Sales") ON 1   
FROM [Adventure Works]  
  
```  
  
 Клиенты, купившие велосипеды:  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Product].[Product Categories].[Category].&[1]}  
, "Internet Sales") ON 1   
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)   
 [Crossjoin &#40;многомерных Выражений&#41;](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin &#40;многомерных Выражений&#41;](../mdx/nonemptycrossjoin-mdx.md)   
 [NonEmpty &#40;многомерных Выражений&#41;](../mdx/nonempty-mdx.md)   
 [IsEmpty &#40;многомерных Выражений&#41;](../mdx/isempty-mdx.md)  
  
  
