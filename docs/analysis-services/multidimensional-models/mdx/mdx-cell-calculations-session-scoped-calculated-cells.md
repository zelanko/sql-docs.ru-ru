---
title: "Создание областью действия сеанса вычисляемых ячеек | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- session-scoped calculated members [MDX]
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c0953df9aa142ce6826e96a3715970d51ec15158
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-cell-calculations---session-scoped-calculated-cells"></a>Вычисления многомерных Выражений ячейки - вычисляемых ячеек с областью действия сеанса
    
> [!IMPORTANT]  
>  Этот синтаксис больше не используется. Вместо него используются присваивания языка многомерных выражений. Дополнительные сведения о присваиваниях см. в разделе [Базовый скрипт многомерных выражений (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md).  
  
 Чтобы создать вычисляемые ячейки, доступные для всех запросов одного и того же сеанса, можно использовать инструкцию [CREATE CELL CALCULATION](../../../mdx/mdx-data-definition-create-cell-calculation.md) или инструкцию [ALTER CUBE](../../../mdx/mdx-data-definition-alter-cube.md) . Обе инструкции обеспечивают одинаковый результат.  
  
## <a name="create-cell-calculation-syntax"></a>Синтаксис CREATE CELL CALCULATION  
  
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
  
## <a name="alter-cube-syntax"></a>Синтаксис ALTER CUBE  
  
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
|Набор элементов уровня|Выражение набора многомерных выражений, которое разрешается к элементам одного уровня. Примером является функция многомерных выражений *Level_Expression*.**Members** . Чтобы включить вычисляемые элементы, используйте функцию многомерных выражений *Level_Expression*.**AllMembers**.<br /><br /> Дополнительные сведения см. в разделе [AllMembers (многомерные выражения)](../../../mdx/allmembers-mdx.md).|  
|Набор потомков|Выражение набора многомерных выражений, которое разрешается к потомкам одного элемента. Примером является функция многомерных выражений **Descendants**(*Member_Expression*, *Level_Expresion*, *Desc_Flag*).<br /><br /> Дополнительные сведения см. в разделе [Descendants (многомерные выражения)](../../../mdx/descendants-mdx.md).|  
  
## <a name="see-also"></a>См. также:  
 [Построение вычислений значений ячеек в многомерном выражении (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations.md)  
  
  

