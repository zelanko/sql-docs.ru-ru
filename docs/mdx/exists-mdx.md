---
description: Exists (многомерные выражения)
title: Exists (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9c879d9091c692cfa7a93490b34c70ad84fa81c4
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92193976"
---
# <a name="exists-mdx"></a>Exists (многомерные выражения)


  Возвращает набор кортежей первого указанного набора, которые один или более раз встречаются во втором наборе. Эта функция вручную выполняет операцию автоматической проверки. Дополнительные сведения о параметре Auto EXISTS см. в разделе Основные [понятия в многомерных выражениях &#40;Analysis Services&#41;](/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services).  
  
 Если указан необязательный параметр \<Measure Group Name> , функция возвращает кортежи, которые существуют с одним или несколькими кортежами из второго набора и эти кортежи со связанными строками в таблице фактов указанной группы мер.  
  
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
  
## <a name="remarks"></a>Remarks  
  
1.  Строки группы мер с мерами, содержащими значения **null, применяют, если указан** аргумент MeasureGroupName. Это разница между этой формой EXISTS и непустой функцией: Если свойство NullProcessing этих мер установлено в значение preserve, это означает, что меры будут показывать значения NULL при выполнении запросов к этой части куба. Непустое значение всегда удаляет кортежи из набора, имеющего значения меры null, тогда как существует с аргументом MeasureGroupName, не будет фильтровать кортежи, имеющие связанные строки группы мер, даже если значения мер равны NULL.  
  
2.  Если используется параметр *MeasureGroupName* , результаты будут зависеть от наличия видимых мер в указанной группе мер. Если в указанной группе мер нет видимых мер, то существует всегда будет возвращать пустой набор, независимо от значений *Set_Expression1* и *Set_Expression2*.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-function-reference-mdx.md)   
 [Перекрестное &#40;&#41;многомерных выражений ](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin &#40;&#41;многомерных выражений ](../mdx/nonemptycrossjoin-mdx.md)   
 [Непустое &#40;&#41;многомерных выражений ](../mdx/nonempty-mdx.md)   
 [&#40;&#41;многомерных выражений ](../mdx/isempty-mdx.md)  
  
