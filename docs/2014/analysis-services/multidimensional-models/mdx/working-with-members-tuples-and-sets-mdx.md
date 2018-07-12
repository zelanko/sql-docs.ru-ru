---
title: Работа с элементами, кортежами и наборами (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], tuples
- member keys [MDX]
- MDX [Analysis Services], sets
- calculated members [MDX]
- members [MDX]
- Multidimensional Expressions [Analysis Services], members
- named sets [MDX]
- Multidimensional Expressions [Analysis Services], tuples
- member functions [MDX]
- sets [MDX]
- MDX [Analysis Services], members
- member names [MDX]
- Multidimensional Expressions [Analysis Services], sets
- tuple functions
- tuples
- set functions [MDX]
ms.assetid: b6ec2439-caef-46d3-9fd7-5f4526cee334
caps.latest.revision: 41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fbd4fa53eb870bc8422dcb80fe019083e773e638
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153265"
---
# <a name="working-with-members-tuples-and-sets-mdx"></a>Работа с элементами, кортежами и наборами (многомерные выражения)
  Многомерные выражения предоставляют функции, возвращающие один или более элементов, кортежей или наборов, или действуют на элемент, кортеж или набор.  
  
## <a name="member-functions"></a>Функции элементов  
 В языке многомерных выражений есть несколько функций для получения элементов из других многомерных сущностей, таких как измерения, уровни или кортежи. Например, функция [FirstChild](/sql/mdx/firstchild-mdx) действует на элемент и возвращает элемент.  
  
 Чтобы найти первый потомок измерения времени, можно указать его явно, как показано в следующем примере.  
  
```  
SELECT [Date].[Calendar Year].[CY 2001] on 0  
FROM [Adventure Works]  
  
```  
  
 Можно также использовать `FirstChild` функция возвращает один и тот же элемент, как показано в следующем примере.  
  
```  
SELECT [Date].[Calendar Year].FirstChild on 0  
FROM [Adventure Works]  
  
```  
  
 Дополнительные сведения о функциях элементов в многомерных выражениях см. в разделе [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="tuple-functions"></a>функции кортежей  
 В языке многомерных выражений есть несколько функций, возвращающих кортежи. Эти функции можно использовать в любом месте, где допускаются кортежи. Например, функция [Item (кортеж) (многомерные выражения)](/sql/mdx/item-tuple-mdx) может использоваться для получения первого кортежа из набора, что удобно, если известно, что набор состоит из единственного кортежа, который нужно передать функции, требующей кортеж в качестве аргумента.  
  
 В следующем примере возвращается первый кортеж из набора кортежей по оси столбцов.  
  
```  
SELECT {  
   ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2003]  
   )  
, ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2004]  
   )  
}.Item(0)  
ON COLUMNS   
FROM [Adventure Works]  
```  
  
 Дополнительные сведения о функциях кортежей см. в разделе [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="set-functions"></a>Функции наборов  
 В языке многомерных выражений есть несколько функций, возвращающих наборы. Чтобы извлечь набор, не обязательно явно перечислять все кортежи в квадратных скобках. Дополнительные сведения о функциях элементов, возвращающих наборы, см. в разделе [Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md). Существует множество дополнительных функций над наборами.  
  
 Оператор «двоеточие» (:) позволяет использовать естественный порядок элементов для создания набора. Например, набор, представленный в следующем примере, содержит четыре кортежа: с первого по четвертый квартал календарного 2002 г.  
  
```  
SELECT   
   {[Calendar Quarter].[Q1 CY 2002]:[Calendar Quarter].[Q4 CY 2002]}   
ON 0  
FROM [Adventure Works]  
```  
  
 Такой же набор можно создать, не используя оператор двоеточия, а указав кортежи, как показано в следующем примере.  
  
```  
SELECT {  
   [Calendar Quarter].[Q1 CY 2002],   
   [Calendar Quarter].[Q2 CY 2002],   
   [Calendar Quarter].[Q3 CY 2002],   
   [Calendar Quarter].[Q4 CY 2002]  
   } ON 0  
FROM [Adventure Works]  
  
```  
  
 Оператор «двоеточие» (:) является инклюзивной функцией. Результирующий набор содержит элементы, указанные с обеих сторон оператора двоеточия.  
  
 Дополнительные сведения о функциях наборов см. в разделе [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="array-functions"></a>Функции массивов  
 Функции массивов обрабатывают набор и возвращают массив. Дополнительные сведения о функциях массивов см. в разделе [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="hierarchy-functions"></a>Функции иерархий  
 Функции иерархий возвращают иерархию, обрабатывая элемент, уровень, иерархию или строку. Дополнительные сведения о функциях иерархий см. в разделе [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="level-functions"></a>Функции уровней  
 Функции уровней возвращают уровень, обрабатывая элемент, уровень или строку. Дополнительные сведения о функциях уровней см. в разделе [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="logical-functions"></a>Логические функции  
 Логическая функция обрабатывает многомерное выражение, возвращая информацию о кортежах, элементах или наборах в выражении. Например, функция [IsEmpty (многомерные выражения)](/sql/mdx/isempty-mdx) оценивает, возвращает ли выражение значение пустой ячейки. Дополнительные сведения о логических функциях см. в разделе [Справочник по функциям многомерных выражений (многомерные выражения)](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="numeric-functions"></a>Числовые функции  
 Числовая функция обрабатывает многомерное выражение, возвращая скалярную величину. Например, функция [Aggregate (многомерные выражения)](/sql/mdx/aggregate-mdx) возвращает скалярную величину, вычисляемую с помощью статистической обработки мер по кортежам в заданном наборе. Дополнительные сведения о числовых функциях см. в разделе [Справочник по функциям многомерных выражений (многомерные выражения)](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="string-functions"></a>Строковые функции  
 Строковая функция обрабатывает многомерное выражение, возвращая строку. Например, функция [UniqueName (многомерные выражения)](/sql/mdx/uniquename-mdx) возвращает строковое значение, включающее в себя уникальное имя измерения, иерархии, уровня или элемента. Дополнительные сведения о строковых функциях см. в разделе [Справочник по функциям многомерных выражений (многомерные выражения)](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="see-also"></a>См. также  
 [Основные понятия многомерных выражений &#40;служб Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)   
 [Основные принципы запросов многомерных Выражений &#40;служб Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](/sql/mdx/mdx-function-reference-mdx)  
  
  
