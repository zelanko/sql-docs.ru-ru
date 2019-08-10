---
title: Exists (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ba2cef1cfb95319cbe0aff827cb251ff7e2317c2
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893609"
---
# <a name="exists-mdx"></a>Exists (многомерные выражения)


  Возвращает набор кортежей первого указанного набора, которые один или более раз встречаются во втором наборе. Эта функция вручную выполняет операцию автоматической проверки. Дополнительные сведения о параметре Auto EXISTS см. [в разделе &#40;основные&#41;понятия в многомерных выражениях Analysis Services](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services).  
  
 Если указано необязательное \<имя группы мер >, функция возвращает кортежи, которые существуют в одном или нескольких кортежах из второго набора, и эти кортежи, имеющие связанные строки в таблице фактов указанной группы мер.  
  
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
  
1.  Строки группы мер с мерами, содержащими значения null, применяют, если указан аргумент MeasureGroupName. Это разница между этой формой EXISTS и непустой функцией: Если свойство NullProcessing этих мер установлено в значение preserve, это означает, что меры будут показывать значения NULL при выполнении запросов к этой части куба. Непустое значение всегда удаляет кортежи из набора, имеющего значения меры null, тогда как существует с аргументом MeasureGroupName, не будет фильтровать кортежи, имеющие связанные строки группы мер, даже если значения мер равны NULL.  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)   
 [Многомерное выражение перекрестного &#40;соединения&#41;](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin &#40;многомерные выражения&#41;](../mdx/nonemptycrossjoin-mdx.md)   
 [Непустое &#40;многомерное выражение&#41;](../mdx/nonempty-mdx.md)   
 [Незаполненное &#40;многомерное выражение&#41;](../mdx/isempty-mdx.md)  
  
  
