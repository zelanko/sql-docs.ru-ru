---
title: EXISTS (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 98f07985b83ae32f02bd3da68d382c8f3fceb0cf
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578256"
---
# <a name="exists-mdx"></a>Exists (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор кортежей первого указанного набора, которые один или более раз встречаются во втором наборе. Эта функция вручную выполняет операцию автоматической проверки. Дополнительные сведения об автоматической проверке, см. в разделе [основные понятия многомерных выражений &#40;служб Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
 Если необязательный \<имя группы мер > указан, функция возвращает кортежи, встречающиеся один или более кортежей второго набора и кортежи, которые имеют связанные строки в таблице фактов заданной группы мер.  
  
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
  
1.  Строки группы мер, содержащих значения null влияют **Exists** Если указан аргумент MeasureGroupName. Разница между данной формой функции Exists и Nonempty заключается в том, что если свойство NullProcessing данных мер имеет значение Preserve, то это означает, что меры будут показывать значения NULL при выполнении запросов для данной части куба. Функция NonEmpty всегда будет удалять кортежи из набора со значениями мер NULL, тогда как функция Exists с аргументом MeasureGroupName не будет отфильтровывать кортежи со связанными строками групп мер, даже если меры имеют значения NULL.  
  
2.  Если *MeasureGroupName* используется параметр, результат будет зависеть, есть ли видимых мер в группе мер, на которую указывает ссылка; Если существует видимых мер в ссылочной группе мер EXISTS всегда возвращает пустой набор, независимо от значения *Set_Expression1* и *Set_Expression2*.  
  
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
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Перекрестное соединение &#40;многомерных Выражений&#41;](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin &#40;многомерных Выражений&#41;](../mdx/nonemptycrossjoin-mdx.md)   
 [NonEmpty &#40;многомерных Выражений&#41;](../mdx/nonempty-mdx.md)   
 [IsEmpty &#40;многомерных Выражений&#41;](../mdx/isempty-mdx.md)  
  
  
