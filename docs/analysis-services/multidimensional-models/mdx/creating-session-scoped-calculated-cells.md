---
title: "Создание вычисляемых ячеек с областью действия сеанса | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "вычисляемые элементы с областью действия сеанса [многомерные выражения]"
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Создание вычисляемых ячеек с областью действия сеанса
    
> [!IMPORTANT]  
>  Этот синтаксис больше не используется. Вместо него используются присваивания языка многомерных выражений. Дополнительные сведения о присваиваниях см. в разделе [Базовый скрипт многомерных выражений (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md).  
  
 Чтобы создать вычисляемые ячейки, доступные для всех запросов одного и того же сеанса, можно использовать инструкцию [CREATE CELL CALCULATION](../Topic/CREATE%20CELL%20CALCULATION%20Statement%20\(MDX\).md) или инструкцию [ALTER CUBE](../Topic/ALTER%20CUBE%20Statement%20\(MDX\).md) . Обе инструкции обеспечивают одинаковый результат.  
  
## Синтаксис CREATE CELL CALCULATION  
  
> [!IMPORTANT]  
>  Этот синтаксис больше не используется. Вместо него используются присваивания языка многомерных выражений. Дополнительные сведения о присваиваниях см. в разделе [Базовый скрипт многомерных выражений (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md).  
  
 Чтобы определить вычисляемую ячейку с областью действия сеанса с помощью инструкции CREATE CELL CALCULATION, используется следующий синтаксис:  
  
```  
CREATE CELL CALCULATION Cube_Expression.<CREATE CELL CALCULATION body clause>  
  
<CREATE CELL CALCULATION body clause> ::=CellCalc_Identifier FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
## Синтаксис ALTER CUBE  
  
> [!IMPORTANT]  
>  Этот синтаксис больше не используется. Вместо него используются присваивания языка многомерных выражений. Дополнительные сведения о присваиваниях см. в разделе [Базовый скрипт многомерных выражений (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md).  
  
 Для определения вычисляемой ячейки с областью действия сеанса с помощью инструкции ALTER CUBE используется следующий синтаксис:  
  
```  
ALTER CUBE Cube_Identifier CREATE CELL CALCULATION  
FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
 Значение выражения `String_Expression` содержит список ортогональных многомерных выражений набора с одним измерением, каждое из которых должно приводиться к одной из следующих категорий наборов:  
  
|Категория|Description|  
|--------------|-----------------|  
|Пустой набор|Выражение набора многомерных выражений, которое разрешается к пустому набору. В этом случае областью вычисляемой ячейки является весь куб.|  
|Одноэлементный набор|Выражение набора многомерных выражений, которое разрешается к единственному элементу.|  
|Набор элементов уровня|Выражение набора многомерных выражений, которое разрешается к элементам одного уровня. Примером является функция многомерных выражений *Level_Expression*.**Members**. Чтобы включить вычисляемые элементы, используйте функцию многомерных выражений *Level_Expression*.**AllMembers**.<br /><br /> Дополнительные сведения см. в разделе [AllMembers (многомерные выражения)](../../../mdx/allmembers-mdx.md).|  
|Набор потомков|Выражение набора многомерных выражений, которое разрешается к потомкам одного элемента. Примером является функция многомерных выражений **Descendants**(*Member_Expression*, *Level_Expresion*, *Desc_Flag*).<br /><br /> Дополнительные сведения см. в разделе [Descendants (многомерные выражения)](../../../mdx/descendants-mdx.md).|  
  
## См. также  
 [Построение вычислений значений ячеек в многомерном выражении (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/building-cell-calculations-in-mdx-mdx.md)  
  
  